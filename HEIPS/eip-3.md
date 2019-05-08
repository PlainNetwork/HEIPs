---
eip: 3
title: `CALLDEPTH` 옵코드 추가(Addition of CALLDEPTH opcode)
author: Martin Holst Swende <martin@swende.se>
status: Deferred
type: Standards Track
category: Core
created: 2015-11-19
---

# Abstract

This is a proposal to add a new opcode, `CALLDEPTH`. The `CALLDEPTH` opcode would return the remaining available call stack depth.
이 제안은 `CALLDEPTH`라는 OPCODE(이하 옵코드)를 추가하기 위함이다.  이 `CALLDEPTH` 옵코드는 남아 있는 콜스택의 깊이를 반환해 준다.

(역, OPCODE란, EVM 실행에 수행하는 명령어셋으로서 가상머신인 EVM내의 연산을 위해 존재한다. 예를 들어 `ADD` 옵코드는 스택에 두개의 값을 꺼내서 더한후 다시 스택에 넣는 옵코드이다.)

# Motivation

There is a limit specifying how deep contracts can call other contracts; the call stack. The limit is currently `256`. If a contract invokes another contract (either via `CALL` or `CALLCODE`), the operation will fail if the call stack depth limit has been reached.

This behaviour makes it possible to subject a contract to a "call stack attack" [1]. In such an attack, an attacker first creates a suitable depth of the stack, e.g. by recursive calls. After this step, the attacker invokes the targeted contract. If the targeted calls another contract, that call will fail. If the return value is not properly checked to see if the call was successfull, the consequences could be damaging.

Example:

1. Contract `A` want's to be invoked regularly, and pays Ether to the invoker in every block.
2. When contract `A` is invoked, it calls contracts `B` and `C`, which consumes a lot of gas. After invocation, contract `A` pays Ether to the caller.
3. Malicious user `X` ensures that the stack depth is shallow before invoking A. Both calls to `B` and `C` fail, but `X` can still collect the reward.

It is possible to defend against this in two ways:

1. Check return value after invocation.
2. Check call stack depth experimentally. A library [2] by Piper Merriam exists for this purpose. This method is quite costly in gas.


[1] a.k.a "shallow stack attack" and "stack attack". However, to be precise, the word ''stack'' has a different meaning within the EVM, and is not to be confused with the ''call stack''.

[2] https://github.com/pipermerriam/ethereum-stack-depth-lib

# Specification

The opcode `CALLDEPTH` should return the remaining call stack depth. A value of `0` means that the call stack is exhausted, and no further calls can be made.

# Rationale

The actual call stack depth, as well as the call stack depth limit, are present in the EVM during execution, but just not available within the EVM. The implementation should be fairly simple and would provide a cheap and way to protect against call stack attacks.

# Implementation

Not implemented.
