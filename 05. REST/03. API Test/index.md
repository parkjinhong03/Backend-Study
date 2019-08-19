# **API 테스팅이란?**

> 직접 API를 테스팅 하고 또한 API가 **기능의 안정성, 성능, 보안** 측면에서 기대치를 충족하는지 **API를 확인**하기 위한 테스팅입니다.

<br>

# **API Testing Method**

1. 언어(Python)에 내장된 **HTTP Client를** 이용한 테스트

    - **requests**
        - requests 모듈을 사용하면 **특정 URI로 HTTP 요청**을 보낼 수 있으므로, 해당 API가 잘 작동하는지 확인할 수 있다.

    - **coreapi**
        - 해당 모듈도 requests 모듈처럼 HTTP 요청을 할 수 있다. 나름 **고수준의 api testing module**이다.

    - **urllib.request**
        - 이 모듈도 가능하지만 위에 나왔던 **requests 사용을 권장**하고 있다.

2. 