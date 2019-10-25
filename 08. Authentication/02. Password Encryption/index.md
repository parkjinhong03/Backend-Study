# **사용자 비밀번호 암호화**

## **비밀번호를 암호화해서 저장해야 하는 이유는?**
1. **외부의 해킹 공격**에 의해 데이터베이스기 노출되었을 경우에 대비해서
2. **내부 인력**에 의해 데이터베이스가 노출되었을 경우에 대비해서

<br>

---
## **암호화 방식**
- **단방향 해시 함수**(one-way hash function)
    - 복호화를 할 수 없는 암호화 알고리즘

    - 온전히 본래의 비밀번호 값을 알지 못하도록 방지하는 데 목적이 있음.
    - **애벌린 효과란?**(avalanche effect)
        - **test password** 와 **test password1** 처럼.
        - 원본은 비슷하지만 **해쉬 함수 값**은 완전히 다른 현상.

    <br>

    > 파이썬 단방향 해시 함수 구현
    ~~~python
    import hashlib                  - 1
    m = hashlib.sha256              - 2
    m.update(b"test password")      - 3
    m.hexdigest()                   - 4
    ~~~

    1. **hashlib** 모듈 임포트. 단방향 해시 암호화 방식을 포함하고 있는 모듈임.
    2. **sha256** 암호 알고리즘 선택.
    3. update 메소드로 **암호화할 값** 등록, 바이트 값을 받으므로 **b prefix** 사용.
    4. 암호화된 값을 **hex(16 진수)** 값으로 읽어 들인다.

<br>

---
## **bcrypt 암호 알고리즘**
위와 같은 함수에도 불구하고 단방향 해시 암호 알고리즘들도 취약한 점이 있고, 충분히 해킹이 가능하다.

<br>

> 해시 알고리즘 해킹
- **rainbow attack**
    - **단방향 해시 알고리즘 해킹** 방법 중 하나이다.
    - 미리 해시 값들을 계산해 놓은 테이블을 이용해서 해시 값을 **역추적해서**   
    본래 값을 찾는 찾아내는 방식이다.
    - 본래 특성상 처리 속도가 **굉장히 빠른 속도로** 임의의 문자열을 해시값으로 바꿀 수 있다.
    - 이런 방식을 이용해서 **패스워드를 추측하는** 해킹 방식이다.

- 따라서 이러한 **취약점을 보완하기** 위해서 일반적으로 **2가지 보완점들이** 사용된다.
    1. **salting**
        - 비밀번호 의외에 추가적으로 랜덤 데이터를 더해서 해시 값을 계산하는 방법
        - 해킹당한 경우에도 어느 부분이 랜덤 값인지 알 수 없게 된다

    2. **키 스트레칭(key stretching)**
        - 기존 단방향 해시 알고리즘들의 실행 속도가 너무 빠르다는 취약점을 보완하기 위해 사용함
        - 단방향 해시 값의 해시 값을 반복하는 방법이다
        - 컴퓨터 성능에 따라 횟수를 추가하여 계속헤서 보완할 수 있다는 장점이 있다.

- **salting과 키 스트레칭**을 구현한 해시 함수인 **bcrypt**가 있다.
    ~~~python
    import bcrypt
    bcrypt.hashpw(b"secret password", bcrypt.gensalt())
    bcrypt.hashpw(b"secret password", bcrypt.gensalt()).hex()
    ~~~

    - **gensalt() 메소드를** 이용하여 개발자조차 알 수 없는 salt 값을 만든다.