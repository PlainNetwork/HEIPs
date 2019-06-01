---
eip: 7
title: DELEGATECALL
author: Vitalik Buterin <v@buterin.com>
translator: Hun Ryu <hunryu@plain.network>
status: Final
type: Standards Track
category: Core
created: 2015-11-15
updated: 2019-06-01
---

### 하드포크
[Homestead](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-606.md)
  
### 매개변수
- 활성화 블록:
  - 메인넷: Block >= 1,150,000 
  - Morden 테스트넷: Block >= 494,000
  - 향후 테스트넷: Block >= 0

### 개요
`0xf4`에 `DELEGATECALL`이라는 새로운 명령어를 추가한다. 이는 `CALLCODE`와 비슷한 개념이나 `DELEGATECALL`은 sender와 value를 부모 스코프(parent scope)에서 자식 스코프(child scope)로 전파한다. `DELEGATECALL`을 통해 생성된 호출은 기존의 호출과 같은 sender와 value를 갖는다.

### 스펙

`DELEGATECALL`: `0xf4`은 6가지 피연산자를 포함한다:
- `gas`: 코드가 실행되기 위해 요구되는 가스량
- `to`: 코드가 실행되었을 시 수신처의 주소
- `in_offset`: 입력값 메모리의 오프셋(offset)
- `in_size`: 입력값의 크기(단위: bytes)
- `out_offset`: 출력값 메모리의 오프셋
- `out_size`: 출력값에 대한 스크래치패드의 크기

#### 가스에 대한 노트
- 기본 집행비는 존재하지 않는다; `gas`가 callee에게 주어지는 총 비용이다.
- `CALLCODE`와 비슷하게 계좌 생성은 절대 발생하지 않기때문에 선금 가스 요금은 항상 `schedule.callGas` + `gas`이다.
- 사용되지 않은 가스는 기존과 동일하게 환급된다.

#### sender에 대한 노트
- `CALLER`와 `VALUE`는 caller와 callee 환경에서 동일하게 행동한다.

#### 기타 노트
- 1024 call depth 제한은 유지된다.

### 근거

자식 코드는 저렴한 가스와 높아진 callstack depth를 제외하면 부모 코드와 동일한 환경에서 시행된다. 그러므로 sender와 value를 부모 스코프에서 자식 스코프로 전파하는 것은 한 컨트랙트가 변형 가능한 소스 코드로서 여타 주소를 저장하기에 매우 간편하게 만든다.

사례 1: 3m gas barrier를 위한 코드 스플릿

```python
~calldatacopy(0, 0, ~calldatasize())
if ~calldataload(0) < 2**253:
    ~delegate_call(msg.gas - 10000, $ADDR1, 0, ~calldatasize(), ~calldatasize(), 10000)
    ~return(~calldatasize(), 10000)
elif ~calldataload(0) < 2**253 * 2:
    ~delegate_call(msg.gas - 10000, $ADDR2, 0, ~calldatasize(), ~calldatasize(), 10000)
    ~return(~calldatasize(), 10000)
...
```

사례 2: 컨트랙트 코드를 저장하기 위한 변형가능한 주소

```python
if ~calldataload(0) / 2**224 == 0x12345678 and self.owner == msg.sender:
    self.delegate = ~calldataload(4)
else:
    ~delegate_call(msg.gas - 10000, self.delegate, 0, ~calldatasize(), ~calldatasize(), 10000)
    ~return(~calldatasize(), 10000)
```
이러한 방법으로 호출된 자식 함수들은 이제 `msg.sender`와 `msg.value`를 자유롭게 참조할 수 있다.

### 가능한 반론
* 호출 데이터의 첫 20 바이트에 sender를 붙임으로써 이 기능을 모사할 수 있다. 그러나, 그럴 경우 코드는 delegated 컨트랙트를 위해 따로 컴파일되어야 하며, delegated context와 raw context에서 함께 사용될 수 없게 된다.
