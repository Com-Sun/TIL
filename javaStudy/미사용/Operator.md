멀티캠퍼스 교육에서 새롭게 자바를 배우게 됐다.
버전을 통일해야 해서 jdk와 이클립스를 새로 설치하는 과정이 있었는데, 학생이 많다보니 제각각 다른 오류가 발생했다.

**이 문서**에선 기억나는 오류와 배웠던 부분 몇 가지를 정리하며 복습을 하려고 한다.

### 환경변수 설정

이클립스 설치 전, 메모장으로 자바 프로그래밍 하는 시간을 가졌었다.

제어판 - 고급시스템 설정 - 환경변수 에 들어가 Path를 새로 만들었다.
새로 추가한 Path는 다음과 같다.

Path:

    C:\Program Files\Java\jdk1.8.0_311\bin

새로운 사용자  변수를 추가했다.

JAVA_HOME :

    C:\Program Files\Java\jdk1.8.0_311

이후 메모장으로 한 프로그래밍.

    package com.multi;

    public class Test{
        public static void main(String[ ] args ) { 
            System.out.println("Hello Java!!!");
        }
    }

이 가장 중요한 것이 저장을 모든파일로 한 후 .java로 저장한다.
그냥 txt파일로 저장하면 오류가 생긴다. 

java파일을 만들었으니 이젠 컴파일 할 단계이다. 인터넷으로 찾아보니 일반적으로 다음의 명령어를 사용한다.

    javac Test.java

그런데 수업에서 사용한 명령어는 달랐다. 위의 명령어를 사용했을 경우 오류가 생겼다. 그 이유를 알아보자.

    public class Hello {
        public static void main(String[] args) {
            System.out.println("Hello world");
        }
    }

바로 위에 있는 Hello 클래스와 그 위에 있는 Test 클래스를 비교해보면 그 이유를 알 수 있다. package com.multi 라는 문장이 있다. 아직 이것에 대한 의미는 모르지만, class 파일이 com\multi 에 존재해야한다. 수업에선 다음의 명령어를 사용하여 새로운 디렉터리를 만들었다.


    javac -d . Test.java

그 결과

    com\multi 
 
 라는 디렉토리에 Test.class 라는 파일이 생성되었다.
 마지막으로 cmd를 이용하여 다음의 명령어를 실행시켰다.

     java com.multi.Test

![](/img/multi0.PNG)

---

### 이클립스 설정

언어부분 다 UTF-8로 바꾸기.
설정 - 검색에서 enc 눌러서 바꾸면 됨.


new - Java Project - 프로젝트 네임에 javademo 다음 finish

패키지 익스플로러 -src - new - class- Package에 java1025(원래는 숫자가 들어가면 안됨)
다음에 Name에 Sample

문자 정렬이 제대로 안 됐을때, ctrl + shift + f 누르면 자동정렬

- [이클립스 단축키](https://iamfreeman.tistory.com/entry/Eclipse-%EB%8B%A8%EC%B6%95%ED%82%A4-%EB%AA%A8%EC%9D%8C-%EC%9D%B4%ED%81%B4%EB%A6%BD%EC%8A%A4-Effective-Eclipse-Shortcut-Keys)

sout +ctrl +space 빠르게 입력
main + 컨트롤 스페이스 누르면 자동 완성


### 표기법 종류

### 실습

실제 프로젝트 클래스 이름은 카멜표기법, 숫자 절대 적으면 안됨. 

public static void : 키워드. 단어에 의미를 부여해서 정의해놓은 단어. or 예약어라고 함. 이클립스에서 예약어에 대해 색을 제공. 예약어는 다른 용도로 사용 불가.

	System.out.println(3); //정수
	System.out.println('3'); //문자 (char)
	System.out.println("3"); //문자열 (string)
    System.out.println(3.0); //실수

위 코드에서 각 3이 저장된 주소는 다르다. 각 숫자는 메모리에 저장이된다.


어플리캐이션을 돌릴 땐 main이라는 메소드가 있어야함. 반드시!
static 부분도 동일하게 필요하다. (why?)


리터럴 (literal) : 그 자체의 값(1, 2, 3... or 'a', 'b' ... ortrue)

변수(variable) : 하나의 값을 저장하기 위한 메모리 공간

데이터 타입(data type) : 값의 종류와 메모리 크기를 결정

자바에서 제공하는 데이터 타입 :

1. 기본 데이터 타입(primitive data type) -c와 비슷

        byte(1), short(2), int (4), long (8) : 정수
        float (4), double(8) : 실수
        char(2) : 문자
        boolean (1) :논리

  
2. 참조 데이터 타입 (references data type)
        
        배열(array), 클래스(class), 인터페이스(interface)


### 시스템에서 인식하는 데이터 타입 크기

byte < short, char < int < long < float < double 

		int numX = 3;
		double numY = 4.5;
		
		System.out.println(numY);
		
		numY = 5; // double = int

위 코드에 numY엔 double이 아닌 int가 대입됨. 원래 맞는 것은 numY = (double)5 가 되어 casting을 하는것이 맞음. 근데 괄호가 없음. 이를 묵시적 형변환이라 함.

묵시적 형변환 : 작은 데이터타입을 큰 데이터 타입으로 변환할 때 발생

명시적 형변환 : 큰 데이터 타입을 작은 데이터 타입으로 변환

    numX = (int)2.6;

위와같이 캐스팅 타입을 명시해 주면 ok. 이 경우 데이터 손실이 발생한다.

	public static void main(String [] args) {
		int numX = 3;
		double numY = 4.5;
		
		System.out.println(numY);
		
		numY = 5; // double = int
		
		numX = (int)2.6;
		System.out.println(numX);
    }

    
결과 : 

    4.5
    2

더블이 아닌 float 이나 다른 경우의 데이터 타입은 어떻게 표현하는가?

    float : 1.5f;
    long : 8l;
    byte numB = 7;
    short numS = 3;


### 연산자

연산자 (operator) : 어떠한 기능을 수행하는 기호 (+, -, *...)

피연산자 (operant) : 연산자의 작업 대상 (변수, 상수, 리터럴, 수식)

연산자 종류 :

    1. 산술연산자 : +, -, *...
    2. 비교연산자 : >, <, !=...
    3. 논리연산자 : &&, ||, !(not)
    4. 삼항연산자 (조건연산자) : 조건식 ? 참  : 거짓
    5. 대입연산자 : =, +=, -=, *=...
    6. 단항연산자 : ++, -- ...


데이터타입이 다른 두 개의 변수를 연산할 경우 데이터 타입이 큰 쪽으로 바뀐다. ex) int + double = double

int = short + short 가된다. why ?

    int데이터 타입 이하끼리 연산이 되면 결과는 무조건 int가 된다.
    (너무 작은 크기라 연산중에 오버플로우가 너무 잘 일어나서)

    int = byte + short
    int = char + short
    int = byte + int
    int = byte + byte

### 연산자 2

    int a = 10;
	int b = 3;
		
	System.out.println(a/b);
	System.out.println((double)(a/b));
	System.out.println((double)a/b);

결과

    3
    3.0
    3.3333333333333335


문자열 연결

		int a = 3;
		int b = 4;
		
		System.out.println(a+b);
		System.out.println(a + "는 3입니다"); //문자열 연결의 의미
		System.out.println("a=" + a); //문자열 연결의 의미
		System.out.println("결과 ="+ (a+b)); //여기서 +가 없으면 오류남

결과 

    7
    3는 3입니다
    a=3
    결과 =7

연산자 연산 순위

		int i = 5;
		int j = 0;
		
		j = ++i; // 전위형 : 값이 참조되기 전에 증가시킨다.
		System.out.println(i);
		System.out.println(j);
		
		i = 5;
		j = 0;
		
		j = i++; // 후위형 : 값이 참조된 후에 증가
		System.out.println(i);
		System.out.println(j);

결과

    6
    6
    6
    5

### 논리연산자


 * true && true => true
 * true && false => false
 * false && true => false
 * false && false => false
 * 
 * true || true => true
 * true || false => true
 * false || true => true
 * false || false => false
 * 
 * !true => false
 * !false => true


논리연산자는 경우에 따라 오른쪽에 있는걸 실행 안할수도 있음.

ex ) && 연산자의 좌변의 false일 경우, ||연산자의 좌면의 true인경우

연산자의 순서 실습

		int x = 4;
		int y = 8;
		int z = 10;
		res = x>y || ++y < z && ++x == y;
		
		System.out.println(x);
		System.out.println(y);
		System.out.println(z);
		System.out.println(res);

결과

    5
    9
    10
    false


### 상수

    	final int NUM =4;

상수 : 한번만 기억할 수 있는 메모리 공간. 
상수명 앞에 final이 붙는다. 상수명은 항상 대문자이다





### print문

    println  : 자동 \n이된다.
    print : \n이 없다. 붙어서 나옴.
    printf : 자바에서 1.4에서 추가된 기능. c에서 배운 %d 같은 형식지정자를 사용할수있음. 이때 문자열 자체를 출력하고싶으면 %%를 사용한다. 쌍따옴표를 출력하고싶으면 \"를 사용한다.


%f : %4.1f : 앞의 4는 전체 자릿수, 뒤의 1은 소숫점 갯수. 이 떄 전체 자릿수는 소숫점을 포함한다.
%-4.1f : 왼쪽 정렬로 표시한다. (숫자 기본은 오른쪽 정렬이다)

boolean : %b에 어떤 값이 있으면 true.

\t : 탭키