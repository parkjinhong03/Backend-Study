# **소켓**이란?

## 1. 소켓의 **사전적 의미**
> 소켓은 사전적으로 **'구멍', '연결', '콘센트'** 라는 의미를 가진다.

> 주로, 전기 부품을 규격에 따라 연결할 수 있게 만들어진 **'구멍 형태의 연결부'** 를 일컫는 단어이다.

>즉, **전기를 공급받을 수 있도록** 전기 공급 인프라 환경에 연결할 수 있게 **만들어진 연결부**이다.

<br>

---
## 2. **네트워크 프로그래밍**에서의 소켓

> 프로그램이 네트워크에서 데이터를 송수신 할 수 있도록, **"네트워크 환경에 연결할 수 있게 만들어진 연결부"** 가 바로 **네트워크 소켓** 입니다.

<br>

- 전기 소켓은 전기를 공급받기 위해 **정해진 규격(110v, 220v)**에 맞게 만들어집니다.

- 이처럼, 네트워크 소켓도 네크워크에 연결하기 위한 소켓 또는 **정해진 규약, 즉 통신을 위한 프로토콜(Protocol)** 에 맞게 만들어져야 합니다.

- 보통 **OSI 7 Layer의 네 번째 계층인 TCP** 상에서 동작하는 소켓을 주로 이용하는데 이를 **'TCP 소켓' 또는 'TCP/IP 소켓'** 이라고 부릅니다.

- 그리고, **UDP에서 동작하는 소켓을 "UDP 소켓"** 이라고 합니다.