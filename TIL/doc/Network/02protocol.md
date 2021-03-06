# **프로토콜**

통신하기 위한 규칙 

## 1. OSI 모델과 TCP/IP 모델

데이터의 송수신은 컴퓨터에서 컴퓨터로 데이터를 보내는 것, 이 때 7개의 계층으로 나누어서 일을 나누는 것

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b05beb5c-07c5-4ecd-8f31-816013685f59/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b05beb5c-07c5-4ecd-8f31-816013685f59/Untitled.png)

## 2. TCP/IP 모델

4계층으로 나누어서 생각 

[OSI7 vs TCP/IP](https://www.notion.so/b71f2100727a47e3bf7e3c45cd027431)

# 캡슐화 역캡슐화

## 1. 캡슐화 , 역캡슐화

- 7계층에서 1계층으로 내려올 때 필요한 정보를 붙여서 내려야 하는데, 이 때 필요한 정보를 헤더라고 한다.
- 헤더에는 데이터를 전달받을 상대방에 대한 정보도 포함되어 있음.
- 이렇게 헤더를 붙여나가는 과정을 캡슐화 라고 함. 반대가 역캡슐화
- 헤더만 붙이다가 2계층인 데이터링크 계층에서는 트레일러도 붙인다. 역캡슐화일 때는 데이터링크에서 트레일러를 제거함
- 트레일러 : 데이터를 전달할 때 데이터의 가장 마지막에 추가하는 정보

```python
VPN *더 찾아보기..

가상통신터널을 만들어 기업 본사나 지사 같은 거점을 연결하여 통신하거나
외부에서 인터넷으로 사내에 접속하는 것

- 인터넷VPN
  - 거점간 접속 : IPsec암호 기술 프로토콜로 접속 
  - 원격 접속 연결 : 외부에서 사용하는 컴퓨터와 사내 네트워크를 연결하기 위한 암호화된 통신로 사용
  모두 일반 인터넷망을 사용 
- IP-VPN
  MPLS라는 기술을 사용하며 인터넷망이 아닌 사업자 전용 폐쇄망 사용 
  따라서 MPLS을 사용하면 해킹, 데이터변조의 위험이 없어 암호화 기능 필요 없음
```

# 퀴즈

1. 통신하기 위한 규칙을 (프로토콜)이라고 한다.
2. ISO라는 국제표준화기구가 ISO 모델을 제정했다
3. TCP/IP 4계층에는 어플리케이션 계층, 전송, 인터넷,네트워크 계층이 있다
4. 데이터를 상대방에게 보낼 때 각 층에서 헤더를 보내는 것을 (캡슐화) 라고 한다