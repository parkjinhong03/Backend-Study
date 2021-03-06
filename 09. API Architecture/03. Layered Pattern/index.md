# **레이어드(Layered Pattern)**
- **Multi-tier 아키텍처 패턴**이라고도 하는 아키텍쳐이다.
- 코드를 **논리적인 부분** 혹은 **역할**에 따라 **독립된 모듈**로 나누어서 구성하는 패턴이다.
- 각 모듈들이 **서로의 의존도**에 따라 **층층이 쌓듯이** 연결되어서 **전체 시스템을 구현**하는 구조이다.
- 일반적으로 보통 다음과 같은 **3개의 레이어**가 존재한다.

<br>

---
## **레이어드 아키텍처**
- **Presentation Layer**

- **Business Layer**

- **Persistence Layer**

<br>

---
## **Presentation Layer**
- 해당 시스템을 사용하는 **사용자** 혹은 **클라이언트 시스템**과 **직접적으로 연결**되는 부분이다.
- **웹사이트** -> **UI** // **백엔드 API** -> **endpoint**
- 따라서 이 부분에서 **API 엔드포인트**를 **정의**하고 **HTTP 요청**을 읽어 들이는 **로직**을 구현한다.
- **그 이상의 역할**은 하지 않고, 실제 시스템이 구현하는 **비즈니스 로직**은 **다음 레이어**로 넘기게 된다.

<br>

---
## **Business Layer**
- 이름 그대로 **비즈니스 로직**을 구현하는 부분이다.
- 실제 시스템이 구현해야 하는 **로직**들을 **이 레이어**에서 구현하게 된다.
- 예를 들어, 사용자가 전달한 ID 값이 이미 존재하는지 확인 후 수락 및 거부를 하는 로직.

<br>

---
## **Persistence Layer**
- **데이터베이스**와 관련된 **로직**을 하는 부분이다.
- **Businees Layer**에서 필요한 데이터 **생성, 수정, 읽기** 등을 처리하여
- 실제로, **데이터베이스**에서 데이터를 **저장, 수정, 읽어들이기**를 하는 역할을 한다.

<br>

---
## **레이어드 아키텍처의 핵심 요소**
- **레이어드 아키텍처**의 핵심 요소는 바로 **단방향 의존성**이다.

- **각각의 레이어**는 오직 자기보다 **하위**에 있는 **레이어**에만 **의존**한다.
    - **Presentation Layer**는 **Business Layer**에게 **의존**하고,
    - **Business Layer**는 **Persistence Layer**에게만 **의존**하게 된다.
    - 반대로 **Business Layer**는 **Presentation Layer**에 대해 완전히 **독립적**이며,
    - **Persistence Layer**는 **Business Layer**이나 **Presentation Layer**에 대해 완전히 **독립적**이다.

- 또 다른 핵심 요소는 **"seperation of concerns"** 이다.
    - 즉, 각 **레이어의 역할**이 **명확**하다는 뜻이다.
    - **Presentation Layer**는 **비즈니스 로직**이 **전혀** 구현되어 있지 않다.
    - **비즈니스 로직**을 처리하기 위해서, **Presentation**은 **Business Layer**의 코드를 **호출**해서 사용해야 한다.
    - 이는 **Business Layer**에서도 마찬가지이다.

<br>

---
## **그러므로...**
- 각 레이어가 서로 **독립적 & 역할 분명** -> 서로에게 끼치는 **영향 최소화** -> **확장 & 수정** 쉬움

- 각 레이어가 완벽하게 **분리** -> **역할 명확** -> 뛰어난 **가독성**

- 또한, **높은 재사용 가능성** 형성 가능
    - 예를 들어, **Business Layer**는 여러 다른 **Presentation Layer**에 **적용**할 수 있다.
    - **Flask API**의 엔드포인트에 적용된 **Business Layer**가
    - **다른 프레임워크**를 사용한 **RPC 엔드포인트**에 사용될 수 있다.

- 마지막으로, 훨씬 더 **수월**해진 **테스트 코드** 구현