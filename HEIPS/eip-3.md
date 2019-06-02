---
eip: 3
title: `CALLDEPTH` 옵코드 추가(Addition of CALLDEPTH opcode)
author: Martin Holst Swende <martin@swende.se>
status: Deferred
type: Standards Track
category: Core
created: 2015-11-19
---

# 초록(Abstract)

This is a proposal to add a new opcode, `CALLDEPTH`. The `CALLDEPTH` opcode would return the remaining available call stack depth.
이 제안은 `CALLDEPTH`라는 OPCODE(이하 옵코드)를 추가하기 위함이다.  이 `CALLDEPTH` 옵코드는 남아 있는 콜스택의 깊이를 반환해 준다.

(역, OPCODE란, EVM 실행에 수행하는 명령어셋으로서 가상머신인 EVM내의 연산을 위해 존재한다. 예를 들어 `ADD` 옵코드는 스택에 두개의 값을 꺼내서 더한후 다시 스택에 넣는 연산을 수행한다.)

# 동기(Motivation)

There is a limit specifying how deep contracts can call other contracts; the call stack. The limit is currently `256`. If a contract invokes another contract (either via `CALL` or `CALLCODE`), the operation will fail if the call stack depth limit has been reached.
컨트랙트에서 다른 컨트랙트들를 호출(call)할때 얼마나 깊게(deep) 할 수 있는지 제한이 있다. 이를 '콜 스택' 이라고하며 256단계까지 제한이 있다. 어떤 컨트랙트에서 `CALL` 또는 `CALLCODE` 를 통해 다른 컨트랙트를 호출하는 동작이 '콜 스택' 깊이에 도달한 경우 실패하게 된다. 
 
This behaviour makes it possible to subject a contract to a "call stack attack" [1]. In such an attack, an attacker first creates a suitable depth of the stack, e.g. by recursive calls. After this step, the attacker invokes the targeted contract. If the targeted calls another contract, that call will fail. If the return value is not properly checked to see if the call was successfull, the consequences could be damaging.
이런 행동을 통해 컨트랙트가 "콜 스택 공격" 받을 수 있다. 이러한 공격에서, 공격자는 우선 적절한 깊이의 스택을 만든다(예, 재귀 호출을 사용). 이후 공격자는 목표 컨트랙트 호출한다. 만약 해당 목표 컨트랙트가 다른컨트랙트를 호출(call)한다면 (이미 스택 한계에 도달하였기 때문에)실패하게 된다. 만약, (컨트랙트 상에서) 해당 호출이 성공했었는지에 대해 제대로 확인하지 않는다면 (트랜잭션) 결과가 피해볼 수 있다.   

Example(예시):

1. Contract `A` want's to be invoked regularly, and pays Ether to the invoker in every block.
    컨트랙트 `A` 는 매 블럭마다 정기적으로 간접호출되어 간접호출자에게 이더를 전송(지불)한다.
2. When contract `A` is invoked, it calls contracts `B` and `C`, which consumes a lot of gas. After invocation, contract `A` pays Ether to the caller.
    컨트랙트 `A`가 간접호출될때, 해당 컨트랙트는 gas를 엄청나게 소모하는 `B`와 `C`를 호출 한다. (컨트랙트에 의한) 간접호출 이후, 컨트랙트 `A`는 호출자에게 이더를 전송한다.
3. Malicious user `X` ensures that the stack depth is shallow before invoking A. Both calls to `B` and `C` fail, but `X` can still collect the reward.
    악의적인 사용자 `X`는 간접호출 하기 이전에 해당 스택 깊이를 (stack depth가 거의 차도록) 얕게 만들어 놓는다. 그렇게 될 경우 `B`와 `C`를 호출하는 동작은 실패하지만, 사용자 `X` 는 여전히 (정기적 간접호출을 통해) 보상을 취할 수 있다.. 

It is possible to defend against this in two ways:
아래 두가지 방법을 통해 해당 공격을 막을 수 있다.

1. Check return value after invocation.
    (재귀적) 호출 이후 반환값을 확인한다. 
2. Check call stack depth experimentally. A library [2] by Piper Merriam exists for this purpose. This method is quite costly in gas.
    콜스택 깊이를 실험적으로 확인다. Piper Merriam의 라이브러리[2]는 이러한 목적을 위해 작성되었지만 해당 방법은 가스소모량이 많다.


[1] a.k.a "shallow stack attack" and "stack attack". However, to be precise, the word ''stack'' has a different meaning within the EVM, and is not to be confused with the ''call stack''.
'얕은 스택 공격' 또는 '스택 공격' 이라함, 정확하게 하기 위해 "스택" 이란 단어는 EVM에서 다른 의미를 가지고 있다. (컴퓨터 용어에서 흔히 쓰는) "콜 스택"과 혼동하지 말아야 한다.

[2] https://github.com/pipermerriam/ethereum-stack-depth-lib

# 스펙(Specification)

The opcode `CALLDEPTH` should return the remaining call stack depth. A value of `0` means that the call stack is exhausted, and no further calls can be made.
`CALLDEPTH` 옵코드는 남아 있는 스택 깊이를 반환한다. 이 반환값이 `0` 인경우는 더이상 사용할 수 있는 콜 스택이 없다는 의미이다. 따라서 더이상 (depth가 깊어지는)호출을 생성할 수 없다.

# 해석(Rationale)

The actual call stack depth, as well as the call stack depth limit, are present in the EVM during execution, but just not available within the EVM. The implementation should be fairly simple and would provide a cheap and way to protect against call stack attacks.
실제 콜 스택 깊이 뿐만 아니라 콜스택 깊이의 제한은 EVM이 실행되는 동안 존재하다. 이 기능에 대한 구현은 매우 단순하고 저렴하며, "콜 스택 공격"으로 부터 방어하기 위한 방법이 되어야 한다. 

# 구현(Implementation)

Not implemented.
