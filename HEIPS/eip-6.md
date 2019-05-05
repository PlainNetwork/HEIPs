---
eip: 6
title: SUICIDE 명령어 변경
author: Hudson Jameson <hudson@hudsonjameson.com>
translator: Hun Ryu <hunryu@plain.network>
status: Final
type: Standards Track
category: Interface
created: 2015-11-22
updated: 2019-05-05
---

### 추상적 개념(Abstract)
EIP-6에서 제안된 솔루션은 이더리움 프로그래밍 언어에서 사용되고 있는 `SUICIDE` 명령어를 `SELFDESTRUCT`로 변경하기 위함이다.

### 동기(Motivation)
정신 건강은 많은 이들에게 매우 중대한 문제이며 사소한 일들로 인해 변화가 발생할 수 있다. 소중한 이를 잃었거나 우울증을 앓고 있는 개발자들은 프로그래밍 언어에서 suicide(자살을 의미)라는 단어를 보지 않는 것만으로도 큰 위안을 얻을 겁니다. 전 세계 약 3억 5천만 명이 우울증으로 인해 고통받고 있습니다. 이더리움 커뮤니티의 생태계를 더욱 확장하길 원한다면 이더리움 프로그래밍 언어의 의미 역시 자주 검토되어야 합니다.

스위스 소재 이더리움 개발 조직인 DEVolution, GmbH는 이와 관련하여 다음과 같은 방식을 추천했습니다:
> "Suicide"는 컨트랙트를 삭제 혹은 종료할 시 사용된다. 그러므로 "suicide" 보다 덜 함축적인 단어인 "self-destruct", "destroy", "terminate" 혹은 "close"로 대체할 것을 추천한다.

Suicide라는 단어를 변경하는 주된 이유는 코드보다 사람이 더 중요하다는 점과 이더리움이 이러한 변화의 필요성을 인지할 만큼 성숙한 프로젝트라는 점을 보여주기 위함이다. 자살은 매우 중대한 사안이다. 그러므로 이더리움 커뮤니티 내에서 우울증을 겪고 있거나 최근 자살로 인해 사랑하는 이를 잃은 사람들에게 더 이상의 악영향을 미치지 않도록 노력해야 한다. 이더리움은 아직 초기 단계의 플랫폼이니 초기에 이러한 긍정적인 변화를 준다면 앞으로의 문제를 최소화할 수 있다.

### 구현 (Implementation)
`SELFDESTRUCT`는 `SUICIDE`를 완전히 대체하기보다 해당 명령어의 대체 레이블(alias)로 추가되었다.
https://github.com/ethereum/solidity/commit/a8736b7b271dac117f15164cf4d2dfabcdd2c6fd
https://github.com/ethereum/serpent/commit/1106c3bdc8f1bd9ded58a452681788ff2e03ee7c
