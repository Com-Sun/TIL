# 가장 간단한 자바 애플리케이션

    public class HelloWorldApp {
        public static void main(String[] args) {
            System.out.println("Hello world!!");
        }
    }

위 코드는  Hello World!! 를 출력하는 코드이다.
가장 쉽고, 간단하다.
그런데, 나는 이 코드를 성공적으로 컴파일 하기 위해 생각보다 많은 오류를 해결해야 했다.

우선 첫 번쨰 오류.

###  Build path specifies execution environment JavaSE-.

    Build path specifies execution environment JavaSE-17. There are no JREs installed in the workspace that are strictly compatible with this environment. Study Build path JRE System Library Problem

원인을 찾아보니 Eclipse에서 내가 설치한 jdk의 버전을 지원하지 않아 생기는 오류였다. 최신 jdk를 설치한 것이 원인으로, 자바의 버전을 다운그레이드하여 해결했다.

다음으로 생긴 두 번째 오류.

### No Java Virtual Machine Was Found After Searching The Following Locations

    A Java Runtime Environment.(JRE) or Java Development Kit (JDK) must be available in order to run Eclipse. No Java virtual machine was found after searching the following locations:C~~

이 오류는 자바를 다운그레이드하며 생긴 오류였다. Eclipse는 원래 내가 설치했던 jdk의 버전 17을 경로로 지정했는데, 삭제해서 찾을 수 없게 된 것이었다. 

해결 방법은 eclpise의 설치 위치로 가서 eclipse.ini를 수정해주면 된다.

    C:\Users\사용자이름\eclipse\java-2021-09\eclipse

eclipse의 위치는 위와 같다.

![](/img/err_0.PNG)

여기서 -vm이라 적혀져 있는 부분 아래의 버전을 수정해주면 오류가 해결된다.

이 과정을 통해 나는 겨우 eclipse를 실행할 수 있었고, 드디어 강의를 따라 코드를 작성했다.

    public class HelloWorld2App {
        public static void main(String[] args) {
            System.out.println("Hello world!!");
        }
    }

그런데 발생해버린 세 번째 오류.

### Launch error : Editor does not contain a main type

![](/img/err_1.PNG)

분명 강의를 똑같이 따라했는데 강의에선 컴파일이 잘 되고, 나는 안 됐다. 이유가 무엇일까 다시 강의를 정독했고, 유일하게 다른 점은 프로젝트 생성 과정에서 source와 class파일을 분리할 것인지 선택하는 부분이었다. 나는 깔끔해 보일 것 같아서 src 파일을 분리헀고, 강의에선 그러지 않았다.

혹시나 하는 마음에 새로운 프로젝트를 만들어 강의와 완전 똑같이 코딩을 하였고, 다행히 나는 성공적으로 Hello World!!를 출력할 수 있었다.

![](/img/helloWorld_0.PNG)

그리고 다음 강의를 통해 왜 위와 같은 오류가 발생했는지 알 수 있었다. 먼저, 강의에선 프로젝트 생성 시"use project folder as root for source and class files"를 체크했다. 이후, HelloWorldApp.java파일을 최상위 디렉터리에 그냥 생성했다.

나의 경우 src와 class파일을 분리해서 프로젝트를 생성했고, 강의와 똑같이 최상위 디렉터리에 .java파일을 생성했다. 당연히 내가 작성한 코드는 src 폴더에 없었고, 이로 인해 오류가 발생했던 것이다.

이번엔 이유를 알았으니, .java 파일을 src 폴더에 만들어서 컴파일을 해보았다. 

아이고야, 그럼에도 불구하고 또 오류가 발생했다.

 마지막 네 번째 오류.

### Must declare a named package because this compilation unit is associated to the named module 'HelloWorld2'

이런 기본적인 HelloWorld도 컴파일 못 하는데 어떻게 다음 강의로 넘어가겠는가. 나는 열심히 구글링을 했고, 원인을 알 수 있었다.

    The "delete module-info.java at your Project Explorer tab" answer is the easiest and most straightforward answer, but

    for those who would want a little more understanding or control of what's happening, the following alternate methods may be desirable;

    make an ever so slightly more realistic application; com.YourCompany.etc or just com.HelloWorld (Project name: com.HelloWorld and class name: HelloWorld)
    or

    when creating the java project; when in the Create Java Project dialog, don't choose Finish but Next, and deselect Create module-info.java file

프로젝트를 생성하며 module-info.java 라는 파일도 같이 생성했는데, 이로 인해 발생한 오류였다.

해결 방법은 다음과 같았다.

1. 모듈이라는 파일을 건들거나

2. 모듈을 아예 없애거나

3. 프로젝트를 새로 만들 때 module-info.java라는 파일을 만드는 것에 동의하지 않는다.

나의 경우 2번을 선택하여 성공적으로 두 번째 Hello World!!를 출력할 수 있었다.

![](/img/helloWorld_1.PNG)


### java의 동작원리 

Hello World!!를 출력하는 과정을 통해 경험적으로 자바의 실행 과정을 공부했다. 이번엔 구조적으로 이를 알아보자.


    public class HelloWorldApp {
        public static void main(String[] args) {
            System.out.println("Hello world!!");
        }
    }

위의 코드는 화면에 Hello World!!를 출력시킨다. 이를 표현하는 단어가 있다. 원인을 나타내는 Source.

code.

약속이라는 측면에서 language.

이 세 가지 단어가 의미하는 것은 같다.

    Hello World!!

두 번째로 살펴볼 것은 출력된 결과물 Hello World!!이다. 이 결과물을 부르는 단어는 application, program이다.

이르 조금 더 자세히 설명해보자.

1. java라는 약속된 문법으로 작성된 sourceCode.java 파일 생성. (위의 경우 Hello World!!를 출력하는 코드. 이는 인간의 언어이다.)

2. 컴파일 과정을 통해 컴퓨터의 언어로 번역.

3. java virtual machine에서 이를 run 함

4. 컴퓨터에서 출력.

![](/img/helloWorld_2.PNG)
출처 : [Open tutorials](https://opentutorials.org/course/3930/26651)

---

### public, static, void, String, args[], Sysout

막상 Hello World를 출렸해는데, 의미를 알 수 없는 단어들이 있다. 각각의 의미를 알아보자.

* public : 메소드의 접근제어자. public은 누구나 이 메소드에 접근할 수 있다.

* static : 메소드에 static 이 지정되어 있는 경우 이 메소드는 인스턴스 생성없이 실행 할 수 있음을 의미

* void : 메소드의 리턴값이 없음(void: 사전적으로 "텅 빈" 이라는 뜻)을 의미

* String : 문자열을 나타내는 자바의 자료형

* args[] : String 자료형에 대한 변수명으로 args 뒤에 []가 있으므로 한 개가 아닌 여러개의 값으로 이루어진 배열임을 의미

* System.out.println : 표준출력으로 데이터를 보내는 자바의 내장 메소드로 println 메소드로 들어오는 문자열 값을 화면에 출력한다.

### main 메소드

프로그램의 시작점.