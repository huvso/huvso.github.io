---
comments: true
title: Python Type Checking
key: 202007011
picture_frame: shadow
tags:
  - Python
---

# Python Type Checking(Guide) -- 20200408
- Reference: <https://realpython.com/python-type-checking/>
- DuckTyping Wiki: <https://ko.wikipedia.org/wiki/%EB%8D%95_%ED%83%80%EC%9D%B4%ED%95%91>

## Contents
```
1. Type Systems
  1-1 Dynamic Typing
  1-2 Static Typing
  1-3 Duck Typing
2. Hello Types
3. Pros and Cons
4. Annotations
  4-1 Function Annotations
  4-2 Variable Annotations
  4-3 Type Comments
  4-4 So, Type Annotations or Type Comments?
5. Playing With Python Types, Part 1
  5-1 Example: A Deck of Cards
  5-2 Sequences and Mappings
  5-3 Type Aliases
  5-4 Functions Without Return Values
  5-5 Example: Play Some Cards
  5-6 The Any Type
6. Type Theory
  6-1 Subtypes
  6-2 Covariant, Contravariant, and Invariant
  6-3 Gradual Typing and Consistent Types
7. Playing With Python Types, Part 2
  7-1 Type Variables
  7-2 Duck Types and Protocols
  7-3 The Optional Type
  7-4 Example: The Object(ive) of the Game
  7-5 Type Hint for Methods
  7-6 Classes as Types
  7-7 Returning self or cls
  7-8 Annotating *args and **kwargs
  7-9 Callables
  7-10 Example: Hearts
8. Static Type Checking
  8-1 The Mypy Project
  8-2 Running Mypy
  8-3 Adding Stubs
  8-4 Typeshed
  8-5 Other Static Type Checkers
  8-6 Using Types at Runtime
9. Conclusion
```


## Object
```
- Type annotations and type hint
  · 타입에 대한 주석과 힌트
- Adding static types to code, both your code adn the code of others
  · 모든 코드에 정적 타입 추가
- Running a static type checker
  · 정적 타입 체커 실행
- Enforcing types at runtime
  · 런타임에 타입 적용
```

## 1. Type Systems
모든 프로그래밍 언어는 각 각의 다른 타입 시스템을 포함하고 있다.

### 1-1. Dynamic Typing
Python은 동적 타입 언어이다. 
이것은 Python 인터프리터가 오직 코드가 실행 될 때 타입 체킹을 한 다는 것과 실행 시간 동안 변수의 타입이 변경 될 수 있음을 의미한다.
다음의 예가 Python의 동적 타입을 증명한다

```python
if False:
    1 + "two"  # This line never runs, so no TypeError is raised
else:
    1 + 2
# result: 3

1 + "two"  # Now this is type checked, and a TypeError is raised
# result: TypeError: unsupported operand type(s) for +: 'int' and 'str'
```

첫 번째 예에서 1 + "two"가 절대 실행되지 않으면 절대 타입은 체크되지 않는다.
두 번째 예에서 Python에서 당신은 integer형과 string형을 결합할 수 없으므로, 1 + "two"가 실행될 때 TypeError가 발생된다.

다음으로, 변수가 타입을 변경 할 수 있는지 알아보자.

```python
thing = "Hello"
print(type(thing))
# result: <class 'str'>

thing = 28.1
print(type(thing))
# result: <class 'float'>
```

type()은 객체의 타입을 반환한다.
이 예에서 thing의 타입은 변경 될 수 있음을 확인 할 수 있으며, Python은 정확하게 타입이 변경 되었음을 인지한다.

### 1-2. Static Typing
정적 타입은 동적 타입과 정반대 되는 개념이다.
정적 타입은 프로그램이 실행되지 않아도 타입 체킹이 수행된다.
C와 Java 같은 정적 타입 언어들은 당신의 프로그램이 컴파일 될 때 타입 체킹이 수행된다.

비록 다른 타입의 변수를 캐스팅하는 메커니즘이 있을 수 있으나 정적 타입에서 변수들은 일반적으로 타입이 변경되지 않는다.

정적 타입 언어의 간단한 예제를 살펴보자. 다음은 Java 코드의 한 부분이다.
```python
String thing;
thing = "Hello";
```

첫 번째 줄은 컴파일 시 thing이라는 이름의 변수가 String 타입으로 바인딩 되었음을 선언하였다.
해당 변수는 다른 타입으로 결코 재 바인딩 될 수 없다.
두 번째 줄에서 thing은 값을 할당 받았다.
이것은 String 객체 외의 값들이 절대 선언될 수 없다.
예를 들어서 만약 당신이 thing = 28.1f으로 선언하면 컴파일러는 양립될 수 없는 타입 때문에 에러를 발생시킬 것이다.

Python은 항상 동적으로 타이핑 된 언어로 남을 것이다.
하지만, PEP 484는 Python 코드에서도 정적 타입 체킹을 가능하도록 하는 Type hint를 소개한다.

대부분의 정적 타입 언어들에서 타입이 작동하는 방식과 달리, Type hint는 스스로 Python이 타입을 강제하도록 하는 것은 아니다. 이름에서 알 수 있듯이 Type hint는 단지 타입을 제안한다.
Type hint를 활용한 정적 유형 검사를 수행하는 다른 도구들을 나중에 소개하도록 하겠다.


### 1-3. Duck Typping(다른 설명으로 대체함)
Python에 대해 이야기 할 때 자주 쓰이는 또 다른 용어는 Duck Typing이다.
이 용어는 "오리처럼 걷고 오리처럼 꽥꽥거리면 오리임에 틀림없다"는 말에서 유래되었다.
객체가 실행이 된 시점에서 해당 method와 attribute를 확인하여 객체의 타입을 확인한다.
덕 타이핑(Duck Typing)이란?

```python
class Duck:
    def quack(self):
        print('꽥꽥')

    def feathuers(self):
        print('오리에게 흰색, 회색 깃털이 있습니다.')

    def fly(self):
        print('오리가 날았지만 곧 떨어집니다.')


class Person:
    def quack(self):
        print('이 사람이 오리를 흉내냅니다.')

    def feathuers(self):
        print('사람은 바닥에서 깃털을 주어서 보여줍니다.')


def in_the_forest(duck):
    duck.quack()
    duck.feathuers()
    duck.fly()


def game():
    donald = Duck()
    john = Person()
    in_the_forest(donald)
    in_the_forest(john)


if __name__ == "__main__":
    game()

# result:
# 꽥꽥
# 오리에게 흰색, 회색 깃털이 있습니다.
# 오리가 날았지만 곧 떨어집니다.
# 이 사람이 오리를 흉내냅니다.
# 사람은 바닥에서 깃털을 주어서 보여줍니다.
# AttributeError: 'Person' object has no attribute 'fly'
```

class Duck과 Person은 quack()와 feathuers()의 동일 method를 가지고 있지만.
Person class의 경우 fly() method를 가지고 있지 않기 때문에 AttributeError가 발생한다.

이러한 duck typing의 경우 타입에 대해 매우 자유롭게 작성 할 수 있다.
하지만 코드 실행 시 자료형 오류나 선언되지 않은 method나 attribute를 찾지 못해 오류가 발생할 수 있다. 이러한 문제들은 개발이 어느 정도 진행 된 뒤 발생 될 가능성이 크며, 해당 오류를 찾는 것이 쉽지 않다.
<<<<<<< HEAD



## 2. Hello Types
이번 장에서는 Type hint를 function에 어떻게 추가 하는지 알아 볼 것이다.
다음의 function은 첫 글자를 대문자화 해주고 장식 라인을 추가하여 텍스트 문자열을 헤드라인 형태로 바꾼다.

```python
def headline(text, align=True):
    if align:
        return f"{text.title()}\n{'-' * len(text)}"
    else: 
        return f" {text.title()} ".center(50, "o")

print(headline("python type checking"))
# result: 
# Python Type Checking
# --------------------

print(headline("python type checking", align=False))
# oooooooooooooo Python Type Checking oooooooooooooo
```

해당 function은 기본적으로 밑줄과 왼쪽 정렬된 헤드라인을 반환한다.
정렬 플래그를 False로 설정하면 o에 감싸져서 중앙에 위치된 헤드라인을 반환하도록 할 수 있다.


function에 대한 타입을 추가하려면 다음과 같이 인수 및 변환 값에 annotation을 달기만 하면 된다.

```python
def headline2(text: str, align: bool = True) -> str:
    if align:
        return f"{text.title()}\n{'-' * len(text)}"
    else: 
        return f" {text.title()} ".center(50, "o")
```

text: str 구문은 text 인수는 str 타입이어야 한다고 말한다.
마찬가지로, 선택적 align 인수는 default를 True의 bool 타입을 가져야 한다.
마지막으로, -> str 구문은 headline2()가 문자열을 반환함을 명시하고 있다.

PEP 8은 다음과 같은 구문을 추천한다

  - 콜론에 대한 기본 규칙은 콜론 앞에는 빈공간을 두지 않고 뒤에는 한 공간을 둔다: text: str
  - = 기호 양 옆에는 공백을 사용하도록 한다: align: bool = True
  - -> 화살표 양 옆에는 공백을 사용하도록 한다: def headline2(...) -> str

이와 같은 Type hint를 추가하는 것은 런타임 효과가 없다. 즉, 그것들은 힌트일 뿐 스스로 시행되지 않는다. 예를 들어, align 인수에 잘못된 유형을 사용하더라도 코드는 문제나 경고 없이 계속 실행된다.

```python
print(headline2("python type checking", align="left"))
# reulst:
# Python Type Checking
# --------------------
```

위와 같은 종류의 오류를 잡기 위해서 static type checker를 사용할 수 있다.
static type checker는 코드가 직접적으로 실행 되지 않아도 타입을 체크 해주는 도구이다.

pycharm과 같은 IDE에서는 이미 type checker가 내장되어 있을 수 있다.
<br/>
<img src="https://github.com/huvso/study/blob/master/python/typeChecking/img/01%20pycharm_type_error.png?raw=true" width="450px" height="180px" title="pycharm_type_error" alt="pycharm_type_error_img"/>
<br/>

타입 체킹을 위한 가장 일반적인 도구는 [**Mypy**](http://mypy-lang.org/)이다.
이 챕터에서는 Mypy에 대한 간단한 설명만을 진행하며, 차 후에 Mypy에 대한 자세한 설명을 할 것이다.

만약 당신의 시스템에 Mypy가 설치되어 있지 않다면 pip를 활용하여 설치 할 수 있다.
```shell
pip install mypy
```

2-2. mypy_test.py 파일에 다음의 코드를 입력하라.
```python
# 2-2. mypy_test.py

def headline(text: str, align: bool = True) -> str:
    if align:
        return f"{text.title()}\n{'-' * len(text)}"
    else:
        return f" {text.title()} ".center(50, "o")

print(headline("python type checking"))
print(headline("use mypy", align="center"))
```
이것은 앞에서 본 코드들과 본질적으로 같은 코드이다.

이제 다음의 코드로 mypy를 실행해보자.
```shell
mypy '.\2-2. mypy_test.py'

# result:
2-2. mypy_test.py:10: error: Argument "align" to "headline" has incompatible type "str"; expected "bool"
Found 1 error in 1 file (checked 1 source file)
```

Type hint를 바탕으로 Mypy는 위 코드에서 10번 라인에서 잘못된 타입을 사용하고 있음을 알려준다.


## 3. Pros and Cons(장·단점)

앞 섹션에서 파이썬에서 type checking이 어떻게 이루어지는지 맛을 보았다.
또한 코드에 type을 추가하는 장정 중 하나인 Type hint가 특정 오류를 파악하는데 도움이 된다는 예제를 살펴보았다.
그 밖의 장점으로는 다음과 같다.

 - **Type hint는 당신의 코드를 문서화하는데 도움이 된다.** 
 전통적으로 함수의 인수에 대해 예상되는 유형을 문서화하려면 docstring을 사용했을 것이다. 이것은 효과가 있지만 docstring에 대한 기준이 없기 때문에(PEP 257에도 불구하고) 그것들은 자동 점검에 쉽게 사용될 수 없다.

 - **Type hint는 IDE들과 linter들의 성능을 향상시킨다.** 
 이것들은 당신의 코드에 대한 정적 분석을 훨씬 쉽게 만들어준다. 
 이는 IDE가 더 나은 코드 완성 및 유사한 기능을 제공 할 수 있게 한다. Type annotation을 통해 PyCharm은 텍스트가 문자임을 알고 이를 바탕으로 구체적인 제안을 할 수 있다.
<br/>
<img src="https://github.com/huvso/study/blob/master/python/typeChecking/img/02%20pycharm_code_completion.png?raw=true" width="450px" height="180px" title="pycharm_type_error" alt="pycharm_type_error_img"/>
<br/>

 - **Type hint는 보다 명확한 아키텍처를 구축하고 유지 관리하는데 도움이 된다.**
 Type hint를 사용하는 행위는 당신의 프로그램의 Type에 대해 생각하도록 강요한다. Python의 역동적인 특성이 큰 자산 중 하나이지만, Duck Typing이나 Overload method들, 또는 복수 Return type에 대해 의식하는 것은 좋은 일이다.

물론 정적 Type checking이 다 좋은 것은 아니다. 개발자가 고려해야 할 단점 또한 있다.

 - **Type hint는 개발자의 시간과 노력이 더해져야 한다.**
 비록 그것이 디버깅하는데 더 적은 시간을 소비할 수 있게 하더라도, 그것은 좀 더 많은 코드를 입력하기 위해 더 많은 시간을 할애 할 것이다.

 - **Type hint는 Modern Python에 적합하다.**
 Annotation은 Python 3.0에서 소개 되었으며, Python 2.7에서는 Type comment를 사용할 수 없다. 그러나 'Variable annotation'과 'Postponed evaluation of type hint'와 같은 개선은 당신이 Python 3.6 또는 3.7을 사용하여 Type cheking을 좀 더 잘 할 수 있다는 것을 의미한다.

 - **Type hint는 시동 시 약간의 패널티가 있다.**
 Typing Module을 사용해야 하는 경우 특히 짧은 스크립트에서 import 시간이 상당히 걸릴 수 있다.

 // TODO -  Measureing Import Time

그래서 당신은 당신의 코드에 있는 정적 타입 체크를 사용해야 하는가?
다행히도 Python은 gradual typing의 개념을 제공한다.
이것은 당신이 점진적으로 당신의 코드에 Type을 도입할 수 있다는 것을 의미한다.
Type hint가 없는 코드는 static type checker에 의해 무시된다.
따라서, 중요한 구성 요소에 Type을 추가하기 시작하고 해당 구성 요소가 가치가 있다면 Type 추가를 계속 진행 할 수 있다.

위의 장·단점을 살펴보면 Type을 추가하는 것은 실행 중인 프로그램이나 프로그램 사용자에게 아무런 영향을 미치지 않는다는 것을 알 수 있다.
Type checking은 개발자로서의 삶을 더 낫고 편리하게 만들기 위한 것이다.

프로젝트에 Type을 추가할 지 여부에 대한 몇 가지 규칙은 다음과 같다.
 
 - Python을 배우기 시작한 지 얼마 안 된 사람이라면 더 많은 경험이 있을 때까지 Type hint의 사용을 자제하라.

 - Type hint는 짤은 일회용 스크립트에서는 거의 사용되지 않는다.

 - 다른 사람이 사용할 라이브러리, 특히 PyPy에 게시된 라이브러리에서 Type hint는 많은 가치를 추가한다. 당신의 라이브러리들을 사용하는 다른 코드들은 적절하게 Type을 체크하기 위해서 이러한 Type hint들을 필요로 한다. Type hint를 사용하는 프로젝트로 
 [cursive_re](https://github.com/Bogdanp/cursive_re/blob/master/cursive_re/exprs.py, "cursive_re link"), 
 [black](https://github.com/psf/black/blob/master/black.py, "black link"), 
 [Real Python Reader](https://github.com/realpython/reader/blob/master/reader/feed.py, "reader link"), 
 [Mypy](https://github.com/python/mypy/blob/master/mypy/build.py, "mypy link")
 가 있다

 - 더 큰 프로젝트에서 Type hint를 입력하면 코드가 어떻게 흐르는지 이해하는 데 도움이 되며 매우 권장된다.
 당신이 다른 사람들과 협력하는 프로젝트에서는 더욱 사용이 권장된다.

 Bernát Gábor의 "[The State of Type Hints in Python](https://www.bernat.tech/the-state-of-type-hints-in-python/, "article link")" 글에서 "**Type hint는 unit test에서 작성될 만한 가치가 있을 때마다 사용해야한다.**"고 권고하였다.
 실제로 Type hint는 코드에서 테스트와 유사한 역할을 한고, 테스트는 개발자가 더 나은 코드를 작성하는데 도움을 준다.

 이제 Python에서 Type checking이 어떻게 작동하는지, 그리고 자신의 프로젝트에서 채택하고 싶은 것인지에 대해 생각해보자.

 이 가이드의 나머지 부분에서는 정적 타입 체커를 실행하는 방법(특히 MyPy에 관하여), Type hint 없는 라이브러리를 사용한 코드에서 Type을 체크하는 방법, 그리고 runtime 시 annotation 사용 방법 에 대해 자세히 다룰 것이다.


# Annotations

 
 
 
 