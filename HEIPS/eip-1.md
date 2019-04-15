---
eip: 1
title: EIP의 목적과 가이드라인
status: Active
type: Meta
author: Ludorum Jeoun <ludy@plain.network> Hun Ryu <hunryu@plain.network>
        https://github.com/PlainNetwork/EIPs/blob/master/EIPS/eip-1.md
created: 2019-04-02
updated: 2019-04-16
---

## Handy EIP
이더리움은 오픈소스 프로젝트입니다. 프로토콜에 대한 새로운 아이디어가 있을때마다 Github의 EIP시스템을 통해 제안되고 논의됩니다. EIP는 이더리움의 역사라고 봐도 무방합니다. 현재 블록체인을 조금이라도 공부해본 이라면 들어봤을 ERC-20, ERC-721을 비롯하여 여타 자잘한 수정사항부터 하드포크와 같이 큰 규모의 변경사항까지 모두 EIP를 통해 논의되고 결정됩니다. EIP는 수 많은 논의와 발전 방향이 담긴 이더리움의 역사책이라 봐도 무방합니다. 그만큼 EIP는 이더리움 관련 문서들 가운데 가장 영향력이 큽니다. 그리고 은근히 재밌고 흥미로운 내용들도 존재합니다. 

이더리움에 대한 공부를 시작할때도 EIP를 순서대로 따라가며 차근차근 익히다보면 이더리움이 어떻게 발전되어 왔고 그 기반이 되는 지식들 역시 습득할 수 있다 생각합니다. 하지만 기존의 EIP는 영어로 작성되어 있고 기반 지식에 대한 해설이 입문자 입장에서 충분하지 않다 보니 한국 사용자들에게 어려운 것은 사실입니다. 또한 기술적인 부분이 다수 포함되어 있어 비개발자에게 어렵게 느껴지는 것도 사실입니다. Handy EIP는 이러한 문제들을 해결하고 더욱 많은 사람들이 이더리움에 대해 공부할 수 있도록 돕기 위해 시작된 오픈소스 프로젝트입니다. 기존 EIP 문서를 그대로 번역하는 것만이 아닌, 흐름이 최대한 원활히 이어지도록 해설과 예시도 포함될 예정입니다.

## EIP가 무엇인가?
비트코인에 BIP가 있듯 이더리움에도 EIP가 있습니다. EIP는 Ethereum Improvement Proposal의 약자로서 이더리움 개선 제안을 뜻합니다. 말그대로 EIP는 이더리움 커뮤니티에 정보를 제공하거나 이더리움의 새로운 기능을 소개하는 설계 문서와 같습니다. EIP는 제안하고자 하는 기능과 이유에 대해 기술적으로 명확히 설명해야 합니다. EIP 작성자는 제안한 EIP에 대해 커뮤니티의 합의를 이끌어내야 하며, 반대의견에 대해 기록해야할 의무가 있습니다. 제 아무리 비탈릭이라 하더라도 EIP를 그냥 통과시킬 순 없습니다. 실제로 비탈릭이 제안한 몇몇 EIP 역시 수 많은 토론을 통해 적용된 바 있습니다.

## 역사

EIP 1 문서는 아미르 타키(Amir Taaki)가 작성한 [Bitcoin's BIP-0001]로부터 파생되었습니다. [Bitcoin's BIP-0001]은 [Python's PEP-0001]로부터 파생된 바 있습니다. EIP 1는 복사되었거나 수정된 것이 대부분입니다. PEP-0001는 EIP와 관련없는 복수의 개발자들에 의해 작성되었기 때문에 EIP와 관련된 제안 사항들은 모두 EIP 편집자들에게 전달해야 합니다.

2015년 12월 7일: EIP 1이 개선되었으며 pull request로 지정되었습니다.

2016년 2월 1일: EIP 1에 편집자들이 추가되었고, 과정에 대한 개선 사항 초안이 생성되었으며 Master 스트림에 병합되었습니다.

2018년 5월 21일: [eips.ethereum.org](https://eips.ethereum.org/)에 적용된 새로운 자동 생성 EIP 디렉터리를 반영한 마이너한 수정이 있었습니다.

2018년 5월 29일: Last Call 과정이 추가되었습니다.

2018년 10월 17일: `updated` 헤더가 도입되었습니다.

EIP 1에 대한 변경 사항들은 [여기](https://github.com/ethereum/EIPs/commits/master/EIPS/eip-1.md)에서 확인할 수 있으며, 또는 해당 EIP의 상단 오른쪽에 위치한 History 버튼을 클릭하여 확인 가능합니다.

## EIP 시스템을 왜 사용하는가?
EIP는 새로운 기능을 제안하는데 요구되는 최우선 메커니즘으로 활용되고, 이슈에 대한 커뮤니티의 기술적 조언을 모우고, 이더리움에 적용되는 설계적 결정들을 문서화하기 위함입니다. EIP는 versioned repository(각 업데이트마다 변경된 히스토리를 저장하는 리포지토리)에 텍스트 파일로 유지될 것이기 때문에  EIP의 변경 사항은 문서화되어 모두 기록으로 남아있습니다.

이더리움을 도입하고자 하는 분들에게 EIP는 실질적인 도입 단계를 추적할 수 있는 매우 유용한 방법입니다. 이상적으로는 그들이 도입한 EIP를 리스트로 남겨두면 좋을 듯합니다. 이를 통해 해당 서비스의 엔드 유저는 해당 서비스의 도입 단계를 보다 쉽게 알 수 있을 겁니다.

## EIP 타입

EIP에는 3가지 타입이 존재합니다:
- **Standard Track EIP** 네트워크 프로토콜, 블록 혹은 거래 증명 방식에 대한 개선 사항, 어플리케이션 규격, 이더리움 기반의 어플리케이션에 대한 상호 운용성 등 이더리움에 전체적으로 영향을 끼치는 모든 개선 사항을 포함합니다. Standard EIP는 아래와 같은 카테고리로 나눠질 수 있습니다. Standard Track EIP는 설계 문서를 작성 후 구현 검증이 끝난 후 이더리움 황서에 업데이트됩니다.
  - **Core** - [EIP5], [EIP101]과 같은 컨센서스 포크를 요구하는 개선 사항 혹은 컨센서스와 크게 상관이 없더라도 [“코어 개발자” 논의 사항](https://github.com/ethereum/pm)과 관련된 사안들이 포함됩니다. [EIP90]을 비롯하여 채굴자/노드 전략 변경 내용이 포함된 [EIP86]의 2, 3, 4번이 그 예시입니다.
  - **Networking** - [devp2p]([EIP8]) 및 [Light Ethereum Subprotocol]을 포함하여 [Whisper] & [Swarm]과 같은 네트워크 프로토콜 스펙에 대한 개선 제안도 포함됩니다.
  - **Interface** - ([EIP6]) 및 [Contract ABIs]와 같은 리네이밍(Renaming)을 포함하여 클라이언트 [API/RPC] 스펙과 표준에 대한 개선 사항입니다. 이는 EIP 리포지토리에 제출 되기 이전에 [interface repo]에서 사전 논의가 되어야 합니다.
  - **ERC** - ([ERC20]) 토큰 표준과 같은 컨트랙트 표준, ([ERC26], [ERC137])과 같은 이름 등록 방식, ([ERC67])과 같은 URI 양식, ([EIP82])과 같은 라이브러리/패키지 포맷, 그리고 ([EIP75], [EIP85])과 같은 지갑 포맷을 포함한 어플리케이션 레벨의 표준입니다.
- **Informational EIP**는 이더리움의 디자인 이슈 혹은 이더리움의 보편적인 가이드라인 및 설명에 대한 제안이며, 새로운 기능은 제안하지 않습니다. Informational EIP는 이더리움 커뮤니티의 합의된 사항이라던지 권고사항이 아니며, 사용자와 개발자는 사실상 이를 무시해도 무관합니다.
- **Meta EIP**는 이더리움 프로세스 혹은 해당 프로세스에 대한 변경 사항을 제안합니다. 모든 Meta EIP는 Process EIP입니다. Process EIP는 Standards Track EIP와 비슷하지만 이더리움 프로토콜 이외의 분야에 적용됩니다. 이더리움 발전에 반영되는 안을 제안할 수 있으나 이더리움의 코드에는 반영되지 않습니다. 또한, 커뮤니티의 합의를 도모해야할 수 있습니다. Informational EIP와는 다르게 이는 권고 사항이며, 사용자들은 이를 무시할 수 없습니다. 프로세스 관련 사항, 가이드라인, 의사 결정 과정에 대한 변경 사항, 그리고 이더리움 개발 도구들에 대한 변경 사항도 이에 포함됩니다.

하나의 EIP에 하나의 중요한 제안 혹은 아이디어만 포함되는 것을 권장합니다. EIP가 하나의 아이디어에 집중되어야 성공할 확률이 높기 때문입니다. 하나의 클라이언트에 대한 변경 사항에 EIP가 요구되지 않지만, 다수의 클라이언트 혹은 다수의 어플리케이션을 위한 표준에 대한 변경 사항에는 EIP가 요구됩니다.

EIP는 최소한의 기준에 부합해야 합니다. 제안의 목적이 뚜렷해야하며 개선 사항에 대한 완벽한 설명이 포함되어야 합니다. 또한, 제안은 프로토콜을 지나치게 혼선시켜서는 안됩니다.

## EIP 워크 플로우

EIP 프로세스엔 2가지 그룹이 존재합니다. 챔피언 혹은 *EIP author*라고 불리는 여러분과 [*EIP editor*](#eip-editors), 그리고 [*Ethereum Core Developers*](https://github.com/ethereum/pm)입니다.

:경고: EIP를 시작하기 전에 아이디를 먼저 점검하면 많은 시간을 절약할 수 있습니다. 여러분의 아이디어가 중복되지 않는지 확인하기 위해 이더리움 커뮤니티에 먼저 물어보세요. 아이디어가 저자 본인에게 좋아보일 순 있으나, 그것이 커뮤니티 전체에 반영될 순 없습니다. 여러분의 아이디어에 대해 토론하기 좋은 채널로는 [the Ethereum subreddit], [the Issues section of this repository], [one of the Ethereum Gitter chat rooms]가 있습니다. 특히 [the Issues section of this repository]는 여러분의 제안에 대해 커뮤니티와 논의하고 공식화된 표준으로 EIP를 시작하기에 최적의 채널입니다.

EIP 저자는 아래에서 설명된 스타일과 포맷을 기반으로 EIP를 작성해야 하고, 적절한 포럼에서 논의를 이끌어 내야하며, 해당 아이디어에 대한 커뮤니티의 합의를 도모해야 합니다. 아래 과정은 성공적인 EIP의 예시입니다:

```
[ WIP ] -> [ DRAFT ] -> [ LAST CALL ] -> [ ACCEPTED ] -> [ FINAL ]
```

위에서 명시된 각 상태에 대한 변경은 EIP 저자에 의해 요청되며 EIP 편집자에 의해 리뷰됩니다. 상태 변경은 pull request를 사용해야 합니다. 여러분의 EIP에 대한 논의를 이어갈 수 있는 링크를 포함해야 합니다. EIP 편집자는 아래 설명된 조건에 따라 해당 요청들을 처리해야 합니다.

* **Active** -- 일부 Informational 및 Process EIP는 목적이 구현과 완성이 아니라면 "Active"라는 상태를 부여받을 수 있습니다. 예시: EIP1
* **Work in progress (WIP)** -- EIP 저자가 아이디어가 지지를 얻을 수 있을 지 여부에 대해 커뮤니티에 물어보았다면 [pull request]로 EIP 드래프트를 작성할 수 있습니다. 어느 정도 구현이 된 경우 커뮤니티가 해당 EIP를 공부하는데 도움을 줄 수 있습니다.
  * :승인: 드래프트 -- 제안된 EIP가 이 단계에서 수용될 경우 EIP 편집자는 EIP 넘버를 부여하고 해당 pull request를 병합할 것입니다. EIP 편집자는 이유없이 EIP를 거부할 수 없습니다.
  * :거부: 드래프트 -- 드래프트 상태에서 거부되는 경우 다음과 같은 이유들이 존재합니다. 해당 제안의 목적이 뚜렷하지 않다. 너무 광범위하다. 기술적으로 오류가 존재한다. 적절한 동기부여가 없다. 이전 버전과 호환되지 않는다. [이더리움 철학](https://github.com/ethereum/wiki/wiki/White-Paper#philosophy)에 벗어난다.
* **Draft** -- 첫 드래프트가 병합된 경우 EIP 저자는 EIP를 더욱 발전시키고 다음 단계로 넘어갈 준비가 될 시점까지 pull request를 통해 드래프트에 변경 사항들을 제출할 수 있습니다. EIP는 드래프트 단계에서 구현이 되어야한 다음 단계로 넘어갈 수 있습니다.
  * :승인: Last Call -- 제안된 EIP가 이 단계에서 수용될 경우 EIP 편집자는 Last Call 상태를 부여하고 평균 14일 정도인 리뷰 종료 날짜(`review-period-end`)를 정합니다.
  * :거부: Last Call -- 드래프트에 중요한 변경 사항이 예상되는 경우 Last Call로 넘어가는 요청이 거부됩니다. Rss 피드에서 불필요한 잡음을 피하기 위해 EIP가 Last Call 단계에 단 한번만 진입하길 원합니다.
* **Last Call** -- 해당 EIP는 https://eips.ethereum.org/ 웹사이트에 등재될 것입니다. ([last-call.xml](/last-call.xml)에서 RSS를 통해 구독이 가능합니다)
  * :승인: Accepted (코어 EIP만 해당) -- Last Call 단계에서 별다른 이슈가 없다면 Accepted 단계로 넘어갑니다.
  * :승인: Final (코어 EIP 제외) -- Last Call 단계에서 별다른 이슈가 없다면 Final 단계로 넘어갑니다.
  * :거부: -- Last Call 단계에서 중요한 변경사항이 존재하거나 기술적으로 큰 이슈가 존재한다면 해당 EIP는 Draft 단계로 복귀됩니다.
* **Accepted (코어 EIP만 해당)** -- 해당 EIP는 이더리움 클라이언트 개발자가 관리합니다. 하드포크의 일환으로 해당 EIP를 클라이언트에 인코딩할 지 여부는 EIP 과정의 일부가 아닙니다.
  * :승인: Final -- Standards Track Core EIP는 최소한 3곳의 이더리움 클라이언트에 반영되어야만 Final 상태로 넘어갈 수 있습니다. 구현이 완료되고 커뮤니티에 의해 채택될 경우 "Final" 상태로 변경됩니다.
* **Final** -- 해당 EIP는 현재 최신 버전에 반영되었다는 것을 의미합니다. Final 상태의 EIP는 오류 수정일 경우에만 업데이트가 가능합니다.

일부 예외적인 상태들 역시 존재합니다.

* **Deferred** -- 미래 진행될 하드 포크를 위해 연기된 코어 EIP입니다.
* **Rejected** -- 본질적으로 완전히 어긋난 EIP 혹은 코어 개발자에 의해 거부된 코어 EIP입니다. 이는 이더리움 프로토콜에 반영되지 않습니다.
* **Active** -- Final과 비슷하지만 EIP 넘버 변경 없이 업데이트될 수 있는 EIP를 의미합니다.
* **Superseded** -- 이전에 Final 상태였으나 더이상 최신 버전으로 여겨지지 않는 EIP를 의미합니다. 또다른 EIP가 Final 상태로 있고 Superseded EIP를 참고할 수 있습니다.

## 성공적인 EIP를 작성하기 위한 방법

EIP는 다음과 같은 사항들을 포함해야 합니다:

- 서론(Preamble) - EIP 넘버, 간략한 설명을 해주는 타이틀(44글자 제한)과 같이 해당 EIP에 대한 메타데이터가 명시된 RFC 822 스타일의 헤더를 포함합니다. [여기](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-1.md#eip-header-preamble)를 클릭하면 이에 대한 자세한 정보를 보실 수 있습니다.
- 개요(Simple Summary) - "간단히 설명할 수 없다면 충분히 이해하고 있는 것이 아니다." 해당 EIP에 대해 비전문가 역시 이해할 수 있을 정도의 간소화된 설명을 포함해야 합니다. 
- 추상적 개념(Abstract) - 200단어 이내로 기술적 이슈를 설명해야 합니다.
- 동기(Motivation) (선택적) - 특히 이더리움 프로토콜을 변경하고자 하는 EIP에 동기는 매우 중요합니다. 기존 프로토콜 스펙이 왜 적절하지 않은 지에 대해 명백히 설명해야 합니다. 충분하지 않은 동기 없이 제출되는 EIP는 거부될 수 있습니다.
- 스펙(Specification) - 새로운 기능에 대한 컴퓨터 공학적인 문법과 의미를 설명하는 기술적 스펙을 포함해야 합니다. 해당 스펙은 기존의 이더리움 플랫폼(cpp-ethereum, go-ethereum, parity, ethereumJ, ethereumjs-lib, 및 [기타](https://github.com/ethereum/wiki/wiki/Clients))과 상호 운용될 수 있는 지에 대해 논의될 수 있을 만큼 자세해야 합니다.
- 근거(Rationale) - 근거는 해당 설계의 동기에 대해 설명하고 왜 이러한 설계가 결정되었는 지에 대해 서술하며 이전 스펙 과정을 구체화합니다. 이 단계에서는 그동안 고려되었던 대안과 관련 작업들을 설명해야 합니다. 해당 기능이 여타 프로그래밍 언어로 어떻게 지원되는 지에 대한 설명도 이에 포함됩니다. 또한, 커뮤니티의 합의에 대한 증거를 제시해야 하고 이전에 논의되었던 중요한 이의 사안들에 대해 논하여야 합니다.
- 호환성(Backwards Compatibility) - 호환성이 불가능한 점을 나타낸 모든 EIP는 비호환성 및 이에 대한 심각성을 서술하는 란을 반드시 포함해야 합니다. 해당 EIP는 이러한 비호환성을 어떠한 방식으로 해결할 지에 대해 반드시 설명해야합니다. 비호환성에 대해 충분히 다뤄지지 않은 EIP는 거부될 수 있습니다.
- 시험 사례(Test Cases) - 컨센서스와 관련된 변경 사항을 포함한 EIP는 시험 사례가 필수로 요구됩니다. 이를 제외한 EIP는 가능한 경우 링크를 포함할 수 있습니다.
- 구현(Implementations) - 기술적 구현은 "Final" 상태를 부여받기 전 반드시 끝나야 한다. 코드를 작성하기 전 스펙과 근거에 대한 합의점을 도출하는 것 역시 가치 있지만, "거친 의견 일치와 작동하는 코드 aka 일단 닥치고 코딩(Rough consensus and running code)"은 API 디테일에 대한 수 많은 논의를 해결하는 데 여전히 유용합니다.
- 저작권 면제 - 모든 EIP는 퍼블릭 도메인이어야 합니다. 저작권 면제에 대한 예시는 이 글의 하단에서 확인할 수 있습니다.

## EIP 포맷과 템플릿

EIP는 [markdown] 포맷으로 작성되어야 합니다.
이미지 파일은 `assets/eip-X` 같이 해당 EIP 내 `assets` 폴더의 서브디렉터리에 포함되어야 합니다. 이미지를 EIP에 링크하는 경우 `../assets/eip-X/image.png`와 같은 관련 링크를 사용하면 됩니다.

## EIP 헤더 서론

각 EIP는 3개의 하이픈(`---`)이 앞뒤로 포함된 RFC 822 스타일의 헤더 서론으로 시작되어야 합니다. 헤더는 아래와 같은 순서로 나타납니다. "*"로 마크된 헤더는 선택적이지만 다른 헤더들은 요구됩니다.

` eip:` <EIP 넘버> (이는 EIP 편집자에 의해 결정되고 부여됩니다)

` title:` <EIP 타이틀>
        
` author:` <저자의 이름 혹은 유저네임, 그리고 이메일>

` * discussions-to:` \<공식적인 논의가 이뤄진 스레드(thread) 링크\>

` status:` <Draft | Last Call | Accepted | Final | Active | Deferred | Rejected | Superseded>

`* review-period-end:` <리뷰 종료 날짜>

` type:` <Standards Track (Core, Networking, Interface, ERC)  | Informational | Meta>

` * category:` <Core | Networking | Interface | ERC>

` created:` <생성된 날짜>

` * updated:` <업데이트된 날짜들>

` * requires:` <요구되는 EIP 넘버>

` * replaces:` <대체되는 EIP 넘버>

` * superseded-by:` <Superseded된 EIP 넘버>

` * resolution:` \<해당 EIP에 대한 결의안 링크\>

다수의 답변이 허용되는 헤더들은 컴마로 구분할 수 있습니다.

날짜를 요구하는 헤더들은 항상 ISO 8601 (yyyy-mm-dd) 포맷을 따릅니다.

#### `author` 헤더

`author` 헤더는 해당 EIP 저자의 이름, 이메일 주소, 혹은 유저네임을 선택적으로 포함해야 합니다. 익명을 선호하는 저자는 유저네임만 사용하거나 성을 제외한 이름을 사용할 수 있습니다. 저자 헤더의 포맷은 다음과 같습니다:

> Random J. User &lt;address@dom.ain&gt;

혹은

> Random J. User (@username)

이메일/깃헙 유저네임이 포함된 경우,

> Random J. User

이메일 주소가 포함되지 않은 경우.

#### `resolution` 헤더
`resolution` 헤더는 Standards Track EIP에만 요구됩니다. 해당 EIP에 대한 선언문이 생성된 여타 웹 사이트 혹은 이메일 메시지에 대한 URL 링크를 포함해야 합니다.

#### `discussions-to` 헤더

EIP가 드래프트인 경우 `discussions-to` 헤더는 해당 EIP에 대해 논의 중인 메일링 리스트 혹은 URL 링크를 연결하기 위해 사용됩니다. 앞서 언급된 바외 같이 EIP에 대해 논의할 수 있는 장은 [Ethereum topics on Gitter](https://gitter.im/ethereum/topics), [Ethereum Magicians](https://ethereum-magicians.org/), [Reddit r/ethereum](https://www.reddit.com/r/ethereum/) 등이 있습니다.

해당 EIP가 저자와 개인적으로 논의 중인 경우 `discussions-to`는 필요하지 않습니다.

또한, `discussions-to`는 깃헙 pull request에 링크를 걸 수 없습니다.

#### `type` 헤더

`type` 헤더는 Standards Track, Meta, Informational과 같은 EIP 타입을 정합니다. 만약 Standards Track인 경우 Core, Networking, Interface, ERC 가운데 하나를 포함해야 합니다.

#### `category` 헤더

`category` 헤더는 EIP의 카테고리를 세분화합니다. 이는 Standards Track인 경우에만 해당합니다.

#### `created` 헤더

`created` 헤더는 해당 EIP가 넘버를 부여받은 날짜를 기록합니다. 이 헤더는 1991-10-02과 같이 yyyy-mm-dd 포맷으로 작성되어야 합니다.

#### `updated` 헤더

`updated` 헤더는 해당 EIP에 대해 중요한 변경 사항이 반영된 날짜를 기록합니다. 이 헤더는 Draft 혹은 Active 상태의 EIP에만 해당됩니다.

#### `requires` 헤더

EIP는 해당 EIP가 기반으로 하는 EIP의 넘버를 표시할 수 있습니다. 

#### `superseded-by` 및 `replaces` 헤더

최신 EIP에 의해 더 이상 필수로 요구되지 않는 EIP인 경우 `superseded-by` 헤더를 포함할 수 있습니다. 해당 헤더에는 최신 EIP의 넘버를 입력합니다. 최신 EIP는 `replaces` 헤더에 대체하기 이전에 사용되던 EIP의 넘버를 포함할 수 있습니다.

## 보조 파일

EIP는 다이어그램과 같은 보조 파일을 포함할 수 있씁니다. 파일의 이름은 EIP-XXXX-Y.ext로 기록되어 있어야 합니다. XXXX는 EIP 넘버이고, Y는 시리얼 넘버(1부터 시작)이며, ext는 png와 같은 실제 파일 형식을 대체합니다.

## EIP 소유권 이전

가끔 새로운 저자에게 EIP의 소유권을 이전하는 경우가 발생합니다. 기존 저자를 이전한 EIP의 공동 저자로 유지하고 싶으나 이는 전적으로 기존 저자의 선택에 달려 있습니다. 소유권 이전이 발생하는 이유는 여러가지 입니다. 저자가 더 이상 기여할 여력이 안되는 경우, 더 이상 흥미를 느끼지 않는 경우, 더 이상 연락이 안되는 경우 등이 존재합니다. 혹은 해당 EIP의 방향성에 대해 더 이상 동의하지 않아서일 수도 있습니다. 이더리움은 모든 EIP에 대해 합의를 이루고자 노력하나 만약 불가능한 경우 이에 상응하는 EIP를 제출할 수 있습니다.

만약 특정 EIP 소유권에 관심있다면 기존 저자 혹은 EIP 편집자에게 메시지를 보내면 됩니다. 만약 기존 저자로부터 답장을 받지 못하는 경우 EIP 편집자가 단독적인 결정을 할 수 있습니다. 단, 이러한 결정은 충분히 되돌려 질 수 있습니다.

## EIP 편집자

현재 EIP 편집자 목록은 다음과 같습니다:

` * 닉 존슨(Nick Johnson) (@arachnid)`

` * 캐시 디트리오(Casey Detrio) (@cdetrio)`

` * 허드슨 제임슨(Hudson Jameson) (@Souptacular)`

` * 비탈릭 뷰테린(Vitalik Buterin) (@vbuterin)`

` * 닉 세이버스(Nick Savers) (@nicksavers)`

` * 마틴 비지(Martin Becze) (@wanderer)`

## EIP 편집자의 의무 사항

새로운 EIP가 들어올때마다 편집자는 다음과 같은 과정을 처리합니다:

- 해당 EIP가 준비되었는지 체크하기 위해 정독합니다. 아이디어가 Final 상태까지 이르지 못할 것 같아 보이더라도 기술적으로 편집자를 이해시킬 수 있어야 합니다.
- 타이틀이 내용을 정확히 설명해야 합니다.
- 스펠링, 문법, 문장 구조 등 기본적인 언어, 깃헙 스타일의 마크다운 형식, 그리고 코드 스타일을 체크해야 합니다.

만약 EIP가 충분히 준비되지 않은 경우 편집자는 자세한 설명이 포함된 수정 사항을 저자에게 제공할 것입니다.

EIP가 리포지터리에 올라갈 준비가 된 경우 편집자는 다음과 같은 과정을 처리합니다:

- EIP 넘버를 부여합니다. 보통 pull request 넘버로 부여되며, 저자가 원할 경우에는 해당 EIP에 대한 논의가 이뤄진 Issue 넘버로 부여될 수 있습니다.

- 관련 pull request를 병합합니다.

- 다음 과정을 설명하는 메시지를 EIP 저자에게 전달합니다.

수 많은 EIP는 이더리움 코드베이스에 작성 권한을 보유한 개발자들에 의해 작성되며 유지되고 있습니다. EIP 편집자들은 EIP 수정 사항을 모니터링하고, 구조, 문법, 스펠링, 마크업 이슈들을 정리합니다.

편집자들은 EIP에 대한 재단을 내리지 않습니다. 편집자들은 그저 행정 및 편집과 관련된 부분을 수행할 뿐입니다.

[EIP5]: https://github.com/ethereum/EIPs/blob/master/EIPS/eip-5.md
[EIP101]: https://github.com/ethereum/EIPs/issues/28
[EIP90]: https://github.com/ethereum/EIPs/issues/90
[EIP86]: https://github.com/ethereum/EIPs/issues/86#issue-145324865
[devp2p]: https://github.com/ethereum/wiki/wiki/%C3%90%CE%9EVp2p-Wire-Protocol
[EIP8]: https://github.com/ethereum/EIPs/blob/master/EIPS/eip-8.md
[Light Ethereum Subprotocol]: https://github.com/ethereum/wiki/wiki/Light-client-protocol
[whisper]: https://github.com/ethereum/go-ethereum/wiki/Whisper-Overview
[swarm]: https://github.com/ethereum/go-ethereum/pull/2959
[API/RPC]: https://github.com/ethereum/wiki/wiki/JSON-RPC
[EIP6]: https://github.com/ethereum/EIPs/blob/master/EIPS/eip-6.md
[contract ABIs]: https://github.com/ethereum/wiki/wiki/Ethereum-Contract-ABI
[interfaces repo]: https://github.com/ethereum/interfaces
[ERC20]: https://github.com/ethereum/EIPs/issues/20
[ERC26]: https://github.com/ethereum/EIPs/issues/26
[ERC137]: https://github.com/ethereum/EIPs/issues/137
[ERC67]: https://github.com/ethereum/EIPs/issues/67
[EIP82]: https://github.com/ethereum/EIPs/issues/82
[EIP75]: https://github.com/ethereum/EIPs/issues/75
[EIP85]: https://github.com/ethereum/EIPs/issues/85
[the Ethereum subreddit]: https://www.reddit.com/r/ethereum/
[one of the Ethereum Gitter chat rooms]: https://gitter.im/ethereum/
[pull request]: https://github.com/ethereum/EIPs/pulls
[formal specification]: https://github.com/ethereum/yellowpaper
[the Issues section of this repository]: https://github.com/ethereum/EIPs/issues
[markdown]: https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet
[Bitcoin's BIP-0001]: https://github.com/bitcoin/bips
[Python's PEP-0001]: https://www.python.org/dev/peps/

## EIP 저작권

저작권과 그와 관련된 권리는 [CC0](https://creativecommons.org/publicdomain/zero/1.0/)를 통해 면제됩니다.

## Handy EIP 저작권
CC-BY-SA
