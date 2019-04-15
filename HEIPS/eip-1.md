---
eip: 1
title: EIP의 목적과 가이드라인
status: Active
type: Meta
author: Ludorum Jeoun <ludy@plain.network> Hun Ryu <hunryu@plain.network>
        https://github.com/PlainNetwork/EIPs/blob/master/EIPS/eip-1.md
created: 2019-04-02
updated: 2019-04-02
---

## Handy EIP
이더리움은 오픈소스 프로젝트입니다. 프로토콜에 대한 새로운 아이디어가 있을때마다 Github의 EIP시스템을 통해 제안되고 논의됩니다. EIP는 이더리움의 역사라고 봐도 무방합니다. 현재 블록체인을 조금이라도 공부해본 이라면 들어봤을 ERC-20, ERC-721을 비롯하여 여타 자잘한 수정사항부터 하드포크와 같이 큰 규모의 변경사항까지 모두 EIP를 통해 논의되고 결정됩니다. EIP는 수 많은 논의와 발전 방향이 담긴 이더리움의 역사책이라 봐도 무방합니다. 그만큼 EIP는 이더리움 관련 문서들 가운데 가장 영향력이 큽니다. 그리고 은근히 재밌고 흥미로운 내용들도 존재합니다. 

이더리움에 대한 공부를 시작할때도 EIP를 순서대로 따라가며 차근차근 익히다보면 이더리움이 어떻게 발전되어 왔고 그 기반이 되는 지식들 역시 습득할 수 있다 생각합니다. 하지만 기존의 EIP는 영어로 작성되어 있고 기반 지식에 대한 해설이 입문자 입장에서 충분하지 않다 보니 한국 사용자들에게 어려운 것은 사실입니다. 또한 기술적인 부분이 다수 포함되어 있어 비개발자에게 어렵게 느껴지는 것도 사실입니다. Handy EIP는 이러한 문제들을 해결하고 더욱 많은 사람들이 이더리움에 대해 공부할 수 있도록 돕기 위해 시작된 오픈소스 프로젝트입니다. 기존 EIP 문서를 그대로 번역하는 것만이 아닌, 흐름이 최대한 원활히 이어지도록 해설과 예시도 포함될 예정입니다.

## EIP가 무엇인가?
비트코인에 BIP가 있듯 이더리움에도 EIP가 있습니다. EIP는 Ethereum Improvement Proposal의 약자로서 이더리움 개선 제안을 뜻합니다. 말그대로 EIP는 이더리움 커뮤니티에 정보를 제공하거나 이더리움의 새로운 기능을 소개하는 설계 문서와 같습니다. EIP는 제안하고자 하는 기능과 이유에 대해 기술적으로 명확히 설명해야 합니다. EIP 작성자는 제안한 EIP에 대해 커뮤니티의 합의를 이끌어내야 하며, 반대의견에 대해 기록해야할 의무가 있습니다. 제 아무리 비탈릭이라 하더라도 EIP를 그냥 통과시킬 순 없습니다. 실제로 비탈릭이 제안한 몇몇 EIP 역시 수 많은 토론을 통해 적용된 바 있습니다.

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

EIP 프로세스엔 2가지 그룹이 존재합니다. 여러분, 즉 챔피언 혹은 *EIP author*, [*EIP editor*](#eip-editors)와 [*Ethereum Core Developers*](https://github.com/ethereum/pm)입니다.

:warning: Before you begin, vet your idea, this will save you time. Ask the Ethereum community first if an idea is original to avoid wasting time on something that will be be rejected based on prior research (searching the Internet does not always do the trick). It also helps to make sure the idea is applicable to the entire community and not just the author. Just because an idea sounds good to the author does not mean it will work for most people in most areas where Ethereum is used. Examples of appropriate public forums to gauge interest around your EIP include [the Ethereum subreddit], [the Issues section of this repository], and [one of the Ethereum Gitter chat rooms]. In particular, [the Issues section of this repository] is an excellent place to discuss your proposal with the community and start creating more formalized language around your EIP.

Your role as the champion is to write the EIP using the style and format described below, shepherd the discussions in the appropriate forums, and build community consensus around the idea. Following is the process that a successful EIP will move along:

```
[ WIP ] -> [ DRAFT ] -> [ LAST CALL ] -> [ ACCEPTED ] -> [ FINAL ]
```

Each status change is requested by the EIP author and reviewed by the EIP editors. Use a pull request to update the status. Please include a link to where people should continue discussing your EIP. The EIP editors will process these requests as per the conditions below.

* **Active** -- Some Informational and Process EIPs may also have a status of “Active” if they are never meant to be completed. E.g. EIP 1 (this EIP).
* **Work in progress (WIP)** -- Once the champion has asked the Ethereum community whether an idea has any chance of support, they will write a draft EIP as a [pull request]. Consider including an implementation if this will aid people in studying the EIP.
  * :arrow_right: Draft -- If agreeable, EIP editor will assign the EIP a number (generally the issue or PR number related to the EIP) and merge your pull request. The EIP editor will not unreasonably deny an EIP.
  * :x: Draft -- Reasons for denying draft status include being too unfocused, too broad, duplication of effort, being technically unsound, not providing proper motivation or addressing backwards compatibility, or not in keeping with the [Ethereum philosophy](https://github.com/ethereum/wiki/wiki/White-Paper#philosophy).
* **Draft** -- Once the first draft has been merged, you may submit follow-up pull requests with further changes to your draft until such point as you believe the EIP to be mature and ready to proceed to the next status. An EIP in draft status must be implemented to be considered for promotion to the next status (ignore this requirement for core EIPs).
  * :arrow_right: Last Call -- If agreeable, the EIP editor will assign Last Call status and set a review end date (`review-period-end`), normally 14 days later.
  * :x: Last Call -- A request for Last Call status will be denied if material changes are still expected to be made to the draft. We hope that EIPs only enter Last Call once, so as to avoid unnecessary noise on the RSS feed.
* **Last Call** -- This EIP will listed prominently on the https://eips.ethereum.org/ website (subscribe via RSS at [last-call.xml](/last-call.xml)).
  * :x: -- A Last Call which results in material changes or substantial unaddressed technical complaints will cause the EIP to revert to Draft.
  * :arrow_right: Accepted (Core EIPs only) -- A successful Last Call without material changes or unaddressed technical complaints will become Accepted.
  * :arrow_right: Final (Not core EIPs) -- A successful Last Call without material changes or unaddressed technical complaints will become Final.
* **Accepted (Core EIPs only)** -- This EIP is in the hands of the Ethereum client developers.  Their process for deciding whether to encode it into their clients as part of a hard fork is not part of the EIP process.
  * :arrow_right: Final -- Standards Track Core EIPs must be implemented in at least three viable Ethereum clients before it can be considered Final. When the implementation is complete and adopted by the community, the status will be changed to “Final”.
* **Final** -- This EIP represents the current state-of-the-art. A Final EIP should only be updated to correct errata.

Other exceptional statuses include:

* **Deferred** -- This is for core EIPs that have been put off for a future hard fork.
* **Rejected** -- An EIP that is fundamentally broken or a Core EIP that was rejected by the Core Devs and will not be implemented.
* **Active** -- This is similar to Final, but denotes an EIP which may be updated without changing its EIP number.
* **Superseded** -- An EIP which was previously final but is no longer considered state-of-the-art. Another EIP will be in Final status and reference the Superseded EIP.

## What belongs in a successful EIP?

Each EIP should have the following parts:

- Preamble - RFC 822 style headers containing metadata about the EIP, including the EIP number, a short descriptive title (limited to a maximum of 44 characters), and the author details. See [below](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-1.md#eip-header-preamble) for details.
- Simple Summary - “If you can’t explain it simply, you don’t understand it well enough.” Provide a simplified and layman-accessible explanation of the EIP.
- Abstract - a short (~200 word) description of the technical issue being addressed.
- Motivation (*optional) - The motivation is critical for EIPs that want to change the Ethereum protocol. It should clearly explain why the existing protocol specification is inadequate to address the problem that the EIP solves. EIP submissions without sufficient motivation may be rejected outright.
- Specification - The technical specification should describe the syntax and semantics of any new feature. The specification should be detailed enough to allow competing, interoperable implementations for any of the current Ethereum platforms (cpp-ethereum, go-ethereum, parity, ethereumJ, ethereumjs-lib, [and others](https://github.com/ethereum/wiki/wiki/Clients).
- Rationale - The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work, e.g. how the feature is supported in other languages. The rationale may also provide evidence of consensus within the community, and should discuss important objections or concerns raised during discussion.
- Backwards Compatibility - All EIPs that introduce backwards incompatibilities must include a section describing these incompatibilities and their severity. The EIP must explain how the author proposes to deal with these incompatibilities. EIP submissions without a sufficient backwards compatibility treatise may be rejected outright.
- Test Cases - Test cases for an implementation are mandatory for EIPs that are affecting consensus changes. Other EIPs can choose to include links to test cases if applicable.
- Implementations - The implementations must be completed before any EIP is given status “Final”, but it need not be completed before the EIP is merged as draft. While there is merit to the approach of reaching consensus on the specification and rationale before writing code, the principle of “rough consensus and running code” is still useful when it comes to resolving many discussions of API details.
- Copyright Waiver - All EIPs must be in the public domain. See the bottom of this EIP for an example copyright waiver.

## EIP Formats and Templates

EIPs should be written in [markdown] format.
Image files should be included in a subdirectory of the `assets` folder for that EIP as follow: `assets/eip-X` (for eip **X**). When linking to an image in the EIP, use relative links such as `../assets/eip-X/image.png`.

## EIP Header Preamble

Each EIP must begin with an RFC 822 style header preamble, preceded and followed by three hyphens (`---`). The headers must appear in the following order. Headers marked with "*" are optional and are described below. All other headers are required.

` eip:` <EIP number> (this is determined by the EIP editor)

` title:` <EIP title>

` author:` <a list of the author's or authors' name(s) and/or username(s), or name(s) and email(s). Details are below.>

` * discussions-to:` \<a url pointing to the official discussion thread\>

` status:` <Draft | Last Call | Accepted | Final | Active | Deferred | Rejected | Superseded>

`* review-period-end:` <date review period ends>

` type:` <Standards Track (Core, Networking, Interface, ERC)  | Informational | Meta>

` * category:` <Core | Networking | Interface | ERC>

` created:` <date created on>

` * updated:` <comma separated list of dates>

` * requires:` <EIP number(s)>

` * replaces:` <EIP number(s)>

` * superseded-by:` <EIP number(s)>

` * resolution:` \<a url pointing to the resolution of this EIP\>

Headers that permit lists must separate elements with commas.

Headers requiring dates will always do so in the format of ISO 8601 (yyyy-mm-dd).

#### `author` header

The `author` header optionally lists the names, email addresses or usernames of the authors/owners of the EIP. Those who prefer anonymity may use a username only, or a first name and a username. The format of the author header value must be:

> Random J. User &lt;address@dom.ain&gt;

or

> Random J. User (@username)

if the email address or GitHub username is included, and

> Random J. User

if the email address is not given.

#### `resolution` header

The `resolution` header is required for Standards Track EIPs only. It contains a URL that should point to an email message or other web resource where the pronouncement about the EIP is made.

#### `discussions-to` header

While an EIP is a draft, a `discussions-to` header will indicate the mailing list or URL where the EIP is being discussed. As mentioned above, examples for places to discuss your EIP include [Ethereum topics on Gitter](https://gitter.im/ethereum/topics), an issue in this repo or in a fork of this repo, [Ethereum Magicians](https://ethereum-magicians.org/) (this is suitable for EIPs that may be contentious or have a strong governance aspect), and [Reddit r/ethereum](https://www.reddit.com/r/ethereum/).

No `discussions-to` header is necessary if the EIP is being discussed privately with the author.

As a single exception, `discussions-to` cannot point to GitHub pull requests.

#### `type` header

The `type` header specifies the type of EIP: Standards Track, Meta, or Informational. If the track is Standards please include the subcategory (core, networking, interface, or ERC).

#### `category` header

The `category` header specifies the EIP's category. This is required for standards-track EIPs only.

#### `created` header

The `created` header records the date that the EIP was assigned a number. Both headers should be in yyyy-mm-dd format, e.g. 2001-08-14.

#### `updated` header

The `updated` header records the date(s) when the EIP was updated with "substantional" changes. This header is only valid for EIPs of Draft and Active status.

#### `requires` header

EIPs may have a `requires` header, indicating the EIP numbers that this EIP depends on.

#### `superseded-by` and `replaces` headers

EIPs may also have a `superseded-by` header indicating that an EIP has been rendered obsolete by a later document; the value is the number of the EIP that replaces the current document. The newer EIP must have a `replaces` header containing the number of the EIP that it rendered obsolete.

## Auxiliary Files

EIPs may include auxiliary files such as diagrams. Such files must be named EIP-XXXX-Y.ext, where “XXXX” is the EIP number, “Y” is a serial number (starting at 1), and “ext” is replaced by the actual file extension (e.g. “png”).

## Transferring EIP Ownership

It occasionally becomes necessary to transfer ownership of EIPs to a new champion. In general, we'd like to retain the original author as a co-author of the transferred EIP, but that's really up to the original author. A good reason to transfer ownership is because the original author no longer has the time or interest in updating it or following through with the EIP process, or has fallen off the face of the 'net (i.e. is unreachable or isn't responding to email). A bad reason to transfer ownership is because you don't agree with the direction of the EIP. We try to build consensus around an EIP, but if that's not possible, you can always submit a competing EIP.

If you are interested in assuming ownership of an EIP, send a message asking to take over, addressed to both the original author and the EIP editor. If the original author doesn't respond to email in a timely manner, the EIP editor will make a unilateral decision (it's not like such decisions can't be reversed :)).

## EIP Editors

The current EIP editors are

` * Nick Johnson (@arachnid)`

` * Casey Detrio (@cdetrio)`

` * Hudson Jameson (@Souptacular)`

` * Vitalik Buterin (@vbuterin)`

` * Nick Savers (@nicksavers)`

` * Martin Becze (@wanderer)`

## EIP Editor Responsibilities

For each new EIP that comes in, an editor does the following:

- Read the EIP to check if it is ready: sound and complete. The ideas must make technical sense, even if they don't seem likely to get to final status.
- The title should accurately describe the content.
- Check the EIP for language (spelling, grammar, sentence structure, etc.), markup (Github flavored Markdown), code style

If the EIP isn't ready, the editor will send it back to the author for revision, with specific instructions.

Once the EIP is ready for the repository, the EIP editor will:

- Assign an EIP number (generally the PR number or, if preferred by the author, the Issue # if there was discussion in the Issues section of this repository about this EIP)

- Merge the corresponding pull request

- Send a message back to the EIP author with the next step.

Many EIPs are written and maintained by developers with write access to the Ethereum codebase. The EIP editors monitor EIP changes, and correct any structure, grammar, spelling, or markup mistakes we see.

The editors don't pass judgment on EIPs. We merely do the administrative & editorial part.

## History

This document was derived heavily from [Bitcoin's BIP-0001] written by Amir Taaki which in turn was derived from [Python's PEP-0001]. In many places text was simply copied and modified. Although the PEP-0001 text was written by Barry Warsaw, Jeremy Hylton, and David Goodger, they are not responsible for its use in the Ethereum Improvement Process, and should not be bothered with technical questions specific to Ethereum or the EIP. Please direct all comments to the EIP editors.

December 7, 2015: EIP 1 has been improved and will be placed as a PR.

February 1, 2016: EIP 1 has added editors, made draft improvements to process, and has merged with Master stream.

March 21, 2018: Minor edits to accommodate the new automatically-generated EIP directory on [eips.ethereum.org](https://eips.ethereum.org/).

May 29, 2018: A last call process was added.

Oct 17, 2018: The `updated` header was introduced.

See [the revision history for further details](https://github.com/ethereum/EIPs/commits/master/EIPS/eip-1.md), which is also available by clicking on the History button in the top right of the EIP.

### Bibliography

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

## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
