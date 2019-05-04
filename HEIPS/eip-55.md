---
eip: 55
title: 대소문자 혼용을통한 주소 인코딩 검사(Mixed-case checksum address encoding)
author: Vitalik Buterin <vitalik.buterin@ethereum.org>, Alex Van de Sande <avsa@ethereum.org>
type: Standards Track
category: ERC
status: Final
created: 2016-01-14
---

# 명세(Specification)

파이썬 코드(Code):

``` python
from ethereum import utils

def checksum_encode(addr): # Takes a 20-byte binary address as input
    o = ''
    v = utils.big_endian_to_int(utils.sha3(addr.hex()))
    for i, c in enumerate(addr.hex()):
        if c in '0123456789':
            o += c
        else:
            o += c.upper() if (v & (2**(255 - 4*i))) else c.lower()
    return '0x'+o

def test(addrstr):
    assert(addrstr == checksum_encode(bytes.fromhex(addrstr[2:])))

test('0x5aAeb6053F3E94C9b9A09f33669435E7Ef1BeAed')
test('0xfB6916095ca1df60bB79Ce92cE3Ea74c37c5d359')
test('0xdbF03B407c01E7cD3CBea99509d93f8DDDC8C6FB')
test('0xD1220A0cf47c7B9Be7A2E6BA89F429762e7b9aDb')

```

In English, convert the address to hex, but if the `i`th digit is a letter (ie. it's one of `abcdef`) print it in uppercase if the `4*i`th bit of the hash of the lowercase hexadecimal address is 1 otherwise print it in lowercase.
이더리움 주소를 16진수(hex)로 변환하였을때(역, 일반적인 Ethereum 주소 0xa1b2...), 이더리움 주소의 'i'번째 자리수가 문자(즉, abcdef 중 한개의 문자)이면서, 그와 동시에 이더리움 주소로 생성한 해시(keccak)값에 해당하는 bit의 '4*i'번이 1인 경우 대문자로 출력한다, 이외에는 소문자로 출력한다.

(역, 이더리움 주소인 "0x123456789abcdef123456789abcdef123456789a"이 있다고 할때, 해당 주소를 keccak함수에 입력값으로 사용하여 얻은 Hash 출력값은 '3ff835c0c5fb4cad9aeb19f97f9646156484b33a0ac2859df467f1b94985b84d'이다. 이더리움 주소의 11번째자리의 글자는 'b'이다. 동일한 위치의 Hash값 글자는 "f"로 bit로 변환하면 1111이다. 
규칙에따라 i번째 글자를 비트로 변환 하였을때 4번째 자리 위치가 1이라면 8이상의 값을 가진다. 즉, keccak Hash의 11번째 값인 "f"가 8 이상이므로 이더리움 주소의 11번째 자리를 대문자로 표기한다. 체크섬이 적용된 주소의 값은 "0x123456789aBCd." 로 시작한다.)

# 필요성(Rational)

장점()Benefits):
- Backwards compatible with many hex parsers that accept mixed case, allowing it to be easily introduced over time
  많은 hex 파서들이 대소문자 혼용 주소를 받아들이는 하위 호환성을 가지고 있어, 시간이 지남에 따라 쉽게 도입될 수 있다.
- Keeps the length at 40 characters
  (기존 이더리움 주소 길이인, )40자 길이를 그대로 유지할 수 있다.
- On average there will be 15 check bits per address, and the net probability that a randomly generated address if mistyped will accidentally pass a check is 0.0247%. This is a ~50x improvement over ICAP, but not as good as a 4-byte check code.
  평균적으로 주소당 15개의 체크비트가 있고 잘못입력된 랜덤하하게 생성된 주소가 체크섬을 통과할 확률은 0.0247% 이다. 이것은 ICAP보다 최대 50배 향상된 것이지만, 4-바이트 체크 코드만큼 좋지 않다.

# 구현(Implementation)

In javascript:<br>자바 스크립트 예시.

```js
const createKeccakHash = require('keccak')

function toChecksumAddress (address) {
  address = address.toLowerCase().replace('0x', '')
  var hash = createKeccakHash('keccak256').update(address).digest('hex')
  var ret = '0x'

  for (var i = 0; i < address.length; i++) {
    if (parseInt(hash[i], 16) >= 8) {
      ret += address[i].toUpperCase()
    } else {
      ret += address[i]
    }
  }

  return ret
}
```

```
> toChecksumAddress('0xfb6916095ca1df60bb79ce92ce3ea74c37c5d359')
'0xfB6916095ca1df60bB79Ce92cE3Ea74c37c5d359'
```

Note that the input to the Keccak256 hash is the lowercase hexadecimal string (i.e. the hex address encoded as ASCII):
참고로 Keccak256 해시의 입력값은 모두 16진 소문자 문자열이다.(즉, ASCII로 인코딩된 16진수 주소)

```
    var hash = createKeccakHash('keccak256').update(Buffer.from(address.toLowerCase(), 'ascii')).digest()
```

# 테스트 케이스(Test Cases)

```
# 모두 대문자(All caps)
0x52908400098527886E0F7030069857D2E4169EE7
0x8617E340B3D01FA5F11F306F4090FD50E238070D
# 모두 소문자(All Lower)
0xde709f2102306220921060314715629080e2fb77
0x27b1fdb04752bbc536007a920d24acb045561c26
# 보통의 주소(Normal)
0x5aAeb6053F3E94C9b9A09f33669435E7Ef1BeAed
0xfB6916095ca1df60bB79Ce92cE3Ea74c37c5d359
0xdbF03B407c01E7cD3CBea99509d93f8DDDC8C6FB
0xD1220A0cf47c7B9Be7A2E6BA89F429762e7b9aDb
```

# 적용(Adoption)

| 지갑(Wallet)              | 체크섬 적용한 주소표시   | 잘못된 대소문자 주소 거부 | 짧은 주소 거부 | 긴주소 거부 |
|--------------------------|--------------------------------|----------------------------|-------------------|------------------|
| Etherwall 2.0.1          | Yes                            | Yes                        | Yes               | Yes              |
| Jaxx 1.2.17              | No                             | Yes                        | Yes               | Yes              |
| MetaMask 3.7.8           | Yes                            | Yes                        | Yes               | Yes              |
| Mist 0.8.10              | Yes                            | Yes                        | Yes               | Yes              |
| MyEtherWallet v3.9.4     | Yes                            | Yes                        | Yes               | Yes              |
| Parity 1.6.6-beta (UI)   | Yes                            | Yes                        | Yes               | Yes              |
| Jaxx Liberty 2.0.0       | Yes                            | Yes                        | Yes               | Yes              |
| Coinomi 1.10             | Yes                            | Yes                        | Yes               | Yes              |
| Trust Wallet             | Yes                            | Yes                        | Yes               | Yes              |

### 대소문자 체크섬 주소 지원 거래소(2017-05-27 기준):

| 거래소(Exchange)| 체크섬 입금 주소 표시 | 잘못된 대소문자 주소 거부 | 짧은 주소 거부 | 긴주소 거부 |
|--------------|----------------------------------------|----------------------------|-------------------|------------------|
| Bitfinex     | No                                     | Yes                        | Yes               | Yes              |
| Coinbase     | Yes                                    | No                         | Yes               | Yes              |
| GDAX         | Yes                                    | Yes                        | Yes               | Yes              |
| Kraken       | No                                     | No                         | Yes               | Yes              |
| Poloniex     | No                                     | No                         | Yes               | Yes              |
| Shapeshift   | No                                     | No                         | Yes               | Yes              |

# 참고(References)

1. EIP 55 issue and discussion https://github.com/ethereum/eips/issues/55
2. Python example by @Recmo https://github.com/ethereum/eips/issues/55#issuecomment-261521584
3. Python implementation in [`ethereum-utils`](https://github.com/pipermerriam/ethereum-utils#to_checksum_addressvalue---text)
4. Ethereumjs-util implementation https://github.com/ethereumjs/ethereumjs-util/blob/75f529458bc7dc84f85fd0446d0fac92d991c262/index.js#L452-L466
5. Swift implementation in [`EthereumKit`](https://github.com/yuzushioh/EthereumKit/blob/master/EthereumKit/Helper/EIP55.swift)
6. Kotlin implementation in [`KEthereum`](https://github.com/walleth/kethereum/tree/master/erc55)
