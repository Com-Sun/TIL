# JAVA 로드맵

![](/img/roadMap_1.PNG)

출처 : [우아한 테크코스 깃허브](https://github.com/woowacourse/back-end-roadmap)


백엔드개발자가 되기 위해선 학습해야할 것이 어마어마하게 많다. 공부의 방향을 명확히 잡지 않고 무작정 시간만 투자한다면 중간에 길을 잃을 가능성이 매우 크다. 나 역시 비전공자로써 독학하며 이를 깨달았다. 다행히 메타인지 과정이 늦지 않았고, 정말 훌륭한 로드맵을 참고하여 학습의 방향을 전환할 수 있었다. 위 사진의 출처는 정말로 유명한 **우아한테크코스**의 백엔드과정 로드맵이다. 그렇기에, 이대로만 따라가면 적어도 실패하지는 않을 것이다. 이 문서엔 내가 학습과정에서 얻은 깨달음이 정리되어있다. 

# JAVA

내가 이 문서를 작성하기 시작한 이유가 있다. 이유는 아주 단순하다. **로드맵이 이해가 가지 않았다.**

로드맵의 가장 처음에 "JAVA"가 있다.  JAVA로부터 뻗어나온 가지는 "Generic", "Varargs"... 등이 있다. 이는 자바 기본서에 잘 설명이 되어있었다. 문제는 다음이다. 분기가 Tools와 JDK로 나뉜다. Tools는 그렇다쳐도, JAVA와 JDK는 왜 가지가 나뉘어있을까? 이전까지 배운 지식에서 JDK는 Java Development kit이었다. 그리고 JAVA는 프로그래밍 언어이다. 두 가지를 나누는 기준은 명확히 무엇일까. 내가 가진 지식으론 두 가지를 구분할 수 없었다. 

이를 해결하기 위해 구글링을 시행했다. 독학을 하면서 느낀 것인데, 구글링은 한글보단 영어로 찾는게 최고다. 그 중에서도 공식 문서를 참고하는게 최고다. 아래에 내가 참고한 자바8 공식문서의 링크를 첨부한다.

[자바8 공식문서](https://docs.oracle.com/javase/8/)

## About the Java Technology

![](/img/java_1.PNG)


나는 공식문서를 찾아보기 전까지 **자바**에 대해 무지했다. 자바란 단순히 프로그래밍 언어라고 생각했다. 하지만 공식문서에선 자바를 Java Technology라 표현했다. 즉, 자바란 프로그래밍 언어인 동시에 플랫폼인 것이다!(별것 아닌것같아도 나에겐 큰 깨달음이었다) 계속 문서를 읽어보자.

    자바 프로그래밍 언어에서 모든 소스코드는 우리가 아는 text형식으로 되어있다. 이는 .java 확장자이다. 이는 javac 컴파일러에 의해 .class 확장자로 바뀐다. .class파일은 java virtual machine이 이해할수 있는 bytecode로 이루어져있다. (프로세서로부터 독립적이다) Java 시작 도구에서 Java Virtual Machine의 인스턴스로 응용프로그램을 실행한다.


![](/img/getStarted-compiler.gif)

    이런 특성으로 인해 같은 class파일이라도 다양한 운영체제에서 동일하게 동작한다.

![](/img/helloWorld.gif)

## The Java Platform

    플랫폼은 프로그램이 실행되는 하드웨어 / 소프트웨어 환경이다. 예를들어 윈도우, 리눅스, 맥 등등이 있다. 대부분의 플랫폼은 운영체제 + 하드웨어의 조합으로 이루어져있다. 자바 플랫폼은 'software-only' 플랫폼이다. 즉, 다른 하드웨어 기반으로 실행되는 소프트웨어전용 플랫폼으로, 다른 플랫폼과는 구별된다.

자바플랫폼은 두 개의 구성요소를 갖는다.

* Java Virtual machine
* Java Application Programming Interface (API)

JVM은 위의 설명으로 대체한다.

API는 유용한 기능을 제공하는 구성요소의 모음집이다. 이는 class와 interface로 그룹화되며, 이러한 라이브러리를 package라한다.

![](/img/getStarted-jvm.gif)

## What can java technology do?

![](/img/java_2.PNG)

* Development Tools : 개발도구는 응용프로그램을 컴파일, 실행, 모니터링, 디버깅 및 문서화하는데 필요한 모든것을 제공한다. 주로 사용할 도구는 javac 컴파일러, 자바 런쳐, javadoc이다.

* API

* Deployment Technologies : JDK 소프트웨어는 최종사용자에게 애플리케이션을 배포하기 위한 표준 매커니즘을 제공한다. (Java Web Start software and Java Plug-In software)

* User Interface Toolkits

* Integration Libraries

여기까지가 Java Technology에 대한 개념이다. 즉, 자바란 자바 프로그래밍언어 + 자바 플랫폼으로 이루어진다. 자바 플랫폼이란 JVM + API이다.

하지만 아직 jdk에대해서는 정확히 모른다. jdk의 개념에 대해 알아보자.

## JRE and JDK

![](/img/java_3.PNG)

오라클은 자바 플랫폼과  SE 제품군에 대한 두 가지 주요 소프트웨어 제품을 제공한다.

Java SE Runtime Environment (JRE) : JRE 는 Java 프로그래밍 언어로 작성된 applet(초소형의 응용프로그램)과 애플리케이션을 실행하는데 필요한 라이브러리, JVM, 그리고 다른 구성요소들을 제공한다. 이 런타임 환경은 애플리케이션을 통해 재분배되어 독립적으로 만들 수 있다.

Java SE Development Kit (JDK) : JDK는 applet과 application 개발에 필요하거나 유용한, 컴파일러 혹은 디버거와같은 CLI 개발도구에 더해 JRE를 포함한다. 즉, JRE의 상위집합이다.

![](/img/java_4.PNG)


여기까지 학습했으면 다시 로드맵으로 돌아가보자.

JAVA라는 뿌리에서 뻗어나온 가지 4개가 보인다. 여기서 Generic, Varargs, 등등... 은 프로그래밍 언어와 관련된 개념이다. 이를 확실히 인지하자.

Tool은 말 그대로 도구이다. 이에대한것은 조금 더 나중에 알아보고 JDK를 살펴보자.

JDK : 바로 위의 Conceptual Diagram 에서 보다시피, JDK의 범위는 어마어마하다. 사실 이 부분이 이해가 잘 안갔는데, 내생각에 JDK에 속하는 JCF 와 Java8을 공부하라는 의미같다. 그럼 먼저 JCF부터 보자.

JCF : 컬렉션 프레임웍이다. 자바 기본서에선 JCF를 '데이터 군을 저장하는 클래스들을 표준화한 설계'라 한다. 공식문서를 살펴보자.

![](/img/java_5.PNG)

JCF는 컬렉션이란 녀석을 조작하기 위한 통합아키텍쳐로, details of their representation과 독립적으로 조작할 수 있다. 프로그래밍 노력은 줄이고 성능은 높인다. (간단하게 사용자의 편의성을 위한 기능인것같다. 개념만 알아두고 학습은 자바 기본서로하자.)

Java8 : Java SE8에서 향상된 기능에 대해 말한다. 람다, Stream API 등등

## 학습 시작

이제 JAVA를 어떤 흐름으로 학습해야하는지 명확히 개요가 잡혔다. 여기까지 개념을 잡는것을 1차 목표로 삼고 공부를 시작하자. 어느정도 학습이 된다면 로드맵의 다음으로 진도를 나가기 위해 새로운 문서로 돌아오겠다.