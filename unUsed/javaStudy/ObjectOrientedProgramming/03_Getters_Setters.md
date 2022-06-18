# 캡슐을 깨는 유혹

지금까지 총 3개의 class를 만들었다.

[Exam](https://github.com/Consome1/JavaPractice/blob/main/StructuredJavaPrj/src/part3_ex2_%EB%A9%94%EC%86%8C%EB%93%9C/Exam.java)

[ExamList](https://github.com/Consome1/JavaPractice/blob/main/StructuredJavaPrj/src/part3_ex2_%EB%A9%94%EC%86%8C%EB%93%9C/ExamList.java)

[Program](https://github.com/Consome1/JavaPractice/blob/main/StructuredJavaPrj/src/part3_ex2_%EB%A9%94%EC%86%8C%EB%93%9C/Program.java)

여기서 Exam 클래스만 살펴보자.

    public class Exam {
        int kor;
        int eng;
        int math;
    }


Exam은 아직 캡슐화되지 않은 상태이다. kor를 kor1로 만들면 외부에서 오류가 생긴다. 

Exam을 캡슐화해보자.

    public class Exam {
        int kor1;
        int eng;
        int math;

        public int getKor() {

            return kor1;
        }

        public int getEng() {

            return eng;
        }

        public int getMath() {

            return math;
        }

        public void setKor(int kor) {
            this.kor1 = kor;
            
        }

        public void setEng(int kor) {
            this.eng = eng;
            
        }

        public void setMath(int kor) {
            this.math = math;
            
        }

    }

ExamList의 코드도 수정하자.

	int kor = exam.getKor();
	int eng = exam.getEng();
	int math = exam.getMath();

    //생략

    exam.setKor(kor);
	exam.setEng(kor);
	exam.setMath(kor);



# Getter/Setter의 용도가 무엇일까?

위에서 바꾼 코드를 보면 솔직히 조금 번거롭다는 생각이든다. 그냥 public으로 사용하면 안될까? 속성명이 바뀔 일은 솔직히 별로 없지 않을까?

답은, 아니다.

위와같은 코드를 사용하는 본질적인 목적은 **데이터 구조**가 변경되는 것 때문이다.

## 구조가 변경된다는 말의 의미는?

    public class Exam {
        public int kor;
        public int eng;
        public int math;

    }

원래의 Exam 클래스가 있다. 그런데 이 시험에대한 추가 정보가 필요한 상황이 발생했다고 하자.

    public class Exam {
        public int kor;
        public int eng;
        public int math;

        private int date; //날짜
        private string name; //시험이름

    }

이렇게 하고 보니 kor, eng, math라는 것들은 과목에 대한 속성이다. 즉,

    public class Subject {
        public int kor;
        public int eng;
        public int math;
    }

    public class Exam {
        public Subject subject;

        private int date; //날짜
        private string name; //시험이름

    }

위와같이 데이터의 구조를 중첩시킬수 있다. 이 경우 kor을 호출하기 위해선 다음과 같이 또 코드를 수정해야한다.

    exam.subject.kor 

위와 같이 데이터 구조를 수정할 때마다 계속 속성을 하나하나 수정하는것은 바람직하지 않다.
하지만 이 상황에서 Getters/Setters를 사용한다면 데이터구조에 영향을 받지 않게 된다.


# Exam클래스의 캡슐화 완성

source - generate getters and setters를 사용하면 쉽게 만들수있다.

완성된 Exam 클래스

    public class Exam {
        int kor;
        int eng;
        int math;
        
        public Exam() {
            this(0,0,0);
        }
        
        public Exam(int kor, int eng, int math) {
            this.kor = kor;
            this.eng = eng;
            this.math = math;
        }
        
        public int getKor() {
            return kor;
        }
        public void setKor(int kor1) {
            this.kor = kor;
        }
        public int getEng() {
            return eng;
        }
        public void setEng(int eng) {
            this.eng = eng;
        }
        public int getMath() {
            return math;
        }
        public void setMath(int math) {
            this.math = math;
        }
        public int total() {

            return kor + eng + math;
        }
        public float avg() {

            return total()/ 3.0f;
        }
        
    }

생성자를 통해 처음부터 값을 대입했다. 
