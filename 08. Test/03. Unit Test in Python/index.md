# **pytest**
- Python3에서는 **unittest**라는 **unit test** 코드를 구현하는 데 사용하는 **모듈이** 이미 포함되어 있다.

- 하지만 우리는 **unittest** 말고 **pytest**라는 모듈을 사용할 것 이다.
    - **unittest**보다 **pytest**가 사용하기에 훨씩 **직관적**이고
    - 또한 **unit test** 코드도 더 **간결**하게 만들 수 있다.

- **pytest 설치**
    ~~~
    pip install pytest
    ~~~

<br>

---
## **들어가기 전에 알아야 할 점들**
- pytest는 **파일 이름 앞 부분에 test_** 라고 되어 있는 파일들만 **테스트 파일로 인식**하고 **실행**한다.
- 함수도 마찬가지로 **이름 앞 부분에 test_** 라고 되어 있는 함수들만 **unit test 함수**로 **인식**하고 **실행**한다.

<br>

---
## **실제 unit test 함수**
~~~python
# test_multiply_by_two.py

def multiply_by_two(x):
    return x * 2

def test_multiply_by_two():
    assert multiply_by_two(4) == 7
~~~
- 다음과 같은 파일에 코드를 작성한 후, **터미널에 pytest 명령어**를 사용하여 실행해 보자.
~~~
$ pytest
~~~
- 그럼 **다음과 같은 내용**이 터미널에 출력될 것 이다.
~~~
======================= test session starts =======================
platform darwin -- Python 3.7.0, pytest-5.2.2, py-1.8.0, pluggy-0.13.0
rootdir: /Users/parkjinhong/Desktop/Hi-Python/01. Flask/00. Example/api
collected 1 item                                


test_multiply_by_two.py F 

============================= FAILURES =============================
_______________________ test_multiply_by_two _______________________

    def test_multiply_by_two():
>       assert multiply_by_two(4) == 7
E       assert 8 == 7
E        +  where 8 = multiply_by_two(4)

test_multiply_by_two.py:6: AssertionError
========================= 1 failed in 0.02s =========================
~~~
- 어느 부분에서 AssertionError가 나는지도 자세히 나오므로 디버깅하기가 수월하다.
- 문제가 되는 부분을 다음과 같이 수정하도록 하자.
~~~python
# test_multiply_by_two.py

def multiply_by_two(x):
    return x * 2

def test_multiply_by_two():
    assert multiply_by_two(4) == 8 # 예상 값대로 수정하도록 하자.
~~~
 - 다시 한번 pytest 명령어를 통해서 unit test를 실행하도록 하자.
 ~~~
 $ pytest
 ~~~
 - 그러면 다음과 같이 unit test가 전부 문제 없이 성공했다는 메시지를 볼 수 있을 것 이다.
~~~
======================== test session starts ========================
platform darwin -- Python 3.7.0, pytest-5.2.2, py-1.8.0, pluggy-0.13.0
rootdir: /Users/parkjinhong/Desktop/Hi-Python/01. Flask/00. Example/api
collected 1 item     

test_multiply_by_two.py .  

========================= 1 passed in 0.03s =========================
~~~