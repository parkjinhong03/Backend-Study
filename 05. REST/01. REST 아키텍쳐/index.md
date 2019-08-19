# REST(Representational State Transfe) 이란?
> **자원을 이름으로 구분하여 해당 자원의 상태를 주고 받는 모든 것을 의미한다.**

<br>

- REST는  기본적으로 **웹의 기존 기술과 HTTP 프로토콜**을 그대로 활용하기 때문에 웹의 장점을 최대한 활용할 수 있는 아키텍처이다.

- 월드 와이드 웹(www)과 같은 **분산 하이퍼미디어 시스템**을 위한 소프트웨어 개발 아키텍처의 한 형식

<br>

# REST의 구체적인 개념

- **HTTP URI**를  통해 자원(Resource)를 명시하고, **HTTP Method(POST, GET, PUT, DELETE)** 를 통해 해당 **자원에 대한 CRUD Operation**을 적용하는 것을 의미한다.

    - 웹 사이트의 이미지, 텍스트, DB 내용 등의 모든 자원에 고유한 ID는 HTTP URI를 부여한다.

    - CRUD Operation
        - Create : 생성(POST)
        - Read : 조회(GET)
        - Update : 수정(PUT)
        - Delete : 삭제(DELETE)
        - HEAD: header 정보 조회(HEAD)

<br>

# REST 구성 요소

1. **자원(Resource): URI**

    - 모든 자원에 **고유한 ID**가 존재하고, 이 자원은 **Server에** 존재한다.
    - 자원을 구분하는 ID는 '/groups/:group_id'와 같은 **HTTP URI**이다.
    - Cilent는 URI를 통해 자원을 지정하고 해당 자원의 상태(정보)에 대한 조작을 Server에 요청한다. 

2. **행위(Verb): HTTP Method**

    - HTTP 프로토콜의 Method를 이용한다.
    - HTTP 프로토콜은 **GET, POST, DELETE, PUT** 와 같은 메서드를 제공한다.

3. **표현 (Representation of Resource)**

    -  Cilent가 자원의 상태에 대한 조작을 요청하면 **Server는 이에 적절한 응답(Representation)** 을 보낸다.
    - REST에서 하나의 자원은 **JSON, XML, TEXT, RSS등** 여러 형태로 나타내어 질 수 있다.
     