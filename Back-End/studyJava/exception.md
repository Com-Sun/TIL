# 예외 처리

## 프로그램 오류

프로그램 오류에는 3가지 종류가 있다.

* 컴파일 에러
* 런타임 에러
* 논리적 에러

컴파일 에러는 컴파일러가 잡아준다. 우리가 살펴볼 것은 런타임 에러이다. 런타임 에러또한 2 가지로 나뉜다. error 와 exception 이다. 

에러 : 스택오버플로우, 메모리 부족 등 심각한 오류

예외 : 발생하더라도 수습할 수 있는 덜 심각한 오류

## 예외 클래스의 계층 구조

자바에선 실행시 발생할 수 있는 오류를 Error 와 Exception 클래스로 정의했다. 즉,

    Object - Throwable - Exception - RuntimeException
    Object - Throwable - Error

위와 같은 계층구조를 갖는다. 다시 한 번 확인하자. Exception 클래스 안에 RuntimeException이 있다.

Exception 클래스 (RuntimeException 제외): 사용자의 실수와 같은 외적인 요인에 의해 발생하는 예외 (클래스 이름 잘못 입력 등)

RuntimeException 클래스 : 프로그래머의 실수로 발생하는 예외

## IllegalArgumentException

숫자야구  프로그램을 만들면서 알게된 Exception 클래스. API를 확인해보자.

![](/img/exception_1.PNG)

## 사용법

[링크](https://fakegrowthup.tistory.com/401?category=984746)를 참고하자. 
