# 데이터링크 레이어 
---
- 키워드 :  이더넷, CSMA/CD, MAC주소, 스위치, 충돌 도메인, 이더넷 표준
- 랜에서 데이터를 주고받기 위한 계층

# 1. 데이터 링크 계층의 역할과 이더넷

### 역할

- 네트워크 장비 간의 신호를 주고 받는 규칙을 정하느 계층
- 랜에서 데이터를 주고받기 위한 계층
- 대표적인 규칙 : 이더넷

### 이더넷

- 랜에서의 규칙
- 여러 컴퓨터에서 동시에 데이터를 허브를 통해 보내게 되면 데이터 충돌이 발생할 수 있음 → CSMA/CD를 사용해서 시점을 늦춤
- CSMA/CD (Carrier Sense Multiple Access with Colision Detection)
=(반송파 감지 다중 접속 및 충돌 탐지)

    ◦ CS : 데이터를 보내려고 하는 컴퓨터가 케이블 신호가 흐르고 있는지 확인

    ◦ MA : 케이블에 데이터가 흐르고 있지 않다면 보내도 좋다

    ◦ CD : 충돌이 발생하고 있는지 확인한다

    →  하지만 효율 문제로 현재는 사용 x, 대신 **스위치** 사용 

# 2. MAC 주소

- **랜 카드를 제조할 때 정해지는  물리적인 주소**
- 전 세계에서 유일!

## 구성

```python
00-23-AE-D9-7A-9A
  
```

- 48비트 숫자로 구성
- 앞의 24는 제조사번호
- 뒤의 24는 랜카드의 고유 번호

## 사용(활용) - 이더넷헤더 ,트레일러

- OSI 모델에서는 데이터링크, TCP/IP 모델에서는 네트워크 계층에서 이더넷 헤더와 트레일러를 붙인다.
- 이더넷헤더 - 데이터 -트레일러 = **프레임**
- 프레임이 네트워크를 통해서 전달되는 것임!

### ⑴ 이더넷 헤더

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f543f67d-45e5-4d33-a14b-6e5a841a7e07/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f543f67d-45e5-4d33-a14b-6e5a841a7e07/Untitled.png)

- 유형 : 이더넷으로 전송되는 상위 계층의 포로토콜

    ex) 0800(IPv4), 0806(ARP), 814C(SNMP over Ethernet)..

### ⑵ 트레일러 (FCS-Frame Check Sequence)

- 데이터 전송 중 오류 발생 확인 용도

### ⑶ 전송 순서

- 헤더랑 트레일러 붙여서 프레임을 만듬
- 비트열 전기신호로 변환하여 네트워크로 전송(물리 계층)
    - 만약 동시에 전송하는 경우 충돌이 감지되면 기다렸다 전송 CSMA/CD
- 허브로 전송시) 모든 포트로 발송
- 데이터를 비트열로 변환
- 목적지 MAC주소가 나와 다르면 파기 아니면 수신
- 수신시) 이더넷 헤더와 트레일러를 분리 (역캡슐화)

# 3. 스위치

- 허브와 달리 데이터 충돌이 발생하지 않는 허브
- 데이터 링크 계층에서 동작
- (= 레이어2 스위치, 스위칭 허브)

## MAC 주소 테이블 (Bridge Table)

**→ 스위치 내부에서 적절한 곳으로 데이터를 보내기 위해 존재하는 데이터 베이스**

- 포트번호와 포트의 MAC 주소가 등록되는 데이터베이스
- 맥 주소 필터링

    ◦ 목적지 주소로 데이터를 발송하는 것

    ◦ 스위치와는 다르게 데이터를 모두 전송하지 않음

- how to? **맥 주소 학습 기능**

    ◦ 목적지 MAC 주소가 추가된 프레임이 전송되었을 때 

    ◦ MAC 주소 테이블에 출발지 주소가 없으면 → MAC 주소를 포트와 함께 등록

- **플러딩**

    ◦ 도착지 주소가 주소 테이블에 없을 때 모든 포트로 전송하는 현상

# 4. 데이터 충돌 제어

## 전이중 통신과 반이중 통신

### ⑴ 전이중 통신 방식

- 데이터의 송 수신을 동시데 통신하는 방식
- 동시에 전송해도 충돌발생 x

### ⑵ 반이중 통신 방식

- 하나의 회선으로 번갈아가면서 통신하는 방식
- 동시 전송 시 충돌발생

### 언제 사용하나요?

- 허브는 반이중방식 b/c 충돌나기 때문
- 스위치는 충돌이 없어서 전이중으로 통신 가능

## 충돌 도메인

- 충돌이 발생 할 때 영향이 미치는 범위
- 허브는 허브에 연결된 모든 범위가 충돌 도메인
- 스위치는 컴퓨터 각각
- 충돌 도메인의 범위가 넓을수록 네트워크가 지연된다

- ARP 프로토콜

    Address Resolution Protocol : 목적지의 컴퓨터의 IP 주소를 사용해서 MAC 주소를 찾는 프로토콜

    - IP 주소를 MAC 주소로 변경
    - ARP 요청을 하고 IP주소를 가진 컴퓨터는 MAC주소를 응답하고, 이것으로 이더넷 프레임을 만든다.
    - 출발지 컴퓨터에는 MAC주소와 IP 주소의 매핑정보를 메모리에 보관하고 이것을 ARP 테이블 이라고 한다.
    - 이후의 통신은 컴퓨터의 ARP 테이블을 참고해서 전송됨

## 이더넷 종류와 특징

- 이더넷은 종류, 통신 속도에 따라 규격으로 분리
- 10BASE5 = 통신속도 10Mbps, BASE = BASEBAND 전송바방식, E

# 퀴즈

1. 이더넷에서 데이터의 충돌을 방지하는 규칙으로 **CSMA/CD** 규칙을 사용한다
2. MAC주소는 (48)비트이다.
3. 이더넷 헤더는 14 바이트로 구성되어 있는데 그 중 MAC 주소가 (6) byte, 출발지 MAC 주소가 (6) byte, 유형이 (2) byte 이다.
4. 데이터 링크 계층에서 데이터의 마지막에 추가되는 것을 (트레일러)라고 한다.
5. 스위치의 포트 번호와 그 포트에 접속하는 컴퓨터에 MAC 주소가 등록되는 데이터베이스를 (MAC 주소 테이블)이라고 한다. 
6. 스위치가 수신 포트 이외의 포트에 데이터를 송신하는 것을 (플러딩) 이라고 한다.
7. (전이중 통신 방식)이란 데이터의 송신과 수신이 동시에 일어나는 통신방식이다
8. (반이중 통신 방식)이란 회선 하나로 송신과 수신을 번갈아가면서 하는 통신 방식이다.
9. 데이터의 충돌이 발생하여 그 영향이 미치는 범위를 (충돌 도메인)이라고 한다.
10. 이더넷 구격 10BASE2 케이블의 최대길이는 (185) 미터이다.