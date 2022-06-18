## 문제

세준이는 기말고사를 망쳤다. 세준이는 점수를 조작해서 집에 가져가기로 했다. 일단 세준이는 자기 점수 중에 최댓값을 골랐다. 이 값을 M이라고 한다. 그리고 나서 모든 점수를 점수/M*100으로 고쳤다.

예를 들어, 세준이의 최고점이 70이고, 수학점수가 50이었으면 수학점수는 50/70*100이 되어 71.43점이 된다.

세준이의 성적을 위의 방법대로 새로 계산했을 때, 새로운 평균을 구하는 프로그램을 작성하시오.

## 입력

첫째 줄에 시험 본 과목의 개수 N이 주어진다. 이 값은 1000보다 작거나 같다. 둘째 줄에 세준이의 현재 성적이 주어진다. 이 값은 100보다 작거나 같은 음이 아닌 정수이고, 적어도 하나의 값은 0보다 크다.

## 출력

첫째 줄에 새로운 평균을 출력한다. 실제 정답과 출력값의 절대오차 또는 상대오차가 10-2 이하이면 정답이다

## 내 코드

    import java.util.Scanner;

    public class Main {
        public static void main(String[] args) {
            Scanner sc = new Scanner(System.in);
            float num = sc.nextFloat();
            float[] numArr = new float[(int)num];

            float max = 0;
            float avg = 0;
            float sum = 0;

            for (int i = 0; i < num; i++) {
                numArr[i] = sc.nextFloat();
            }

            for (int i = 0; i < num; i++) {
                if (max < numArr[i]) {
                    max = numArr[i];
                }

            } // end for

            for (int i = 0; i < num; i++) {
                numArr[i] = (numArr[i] / max) * 100;
                sum += numArr[i];
            }

            
            avg =  sum /  num;

            System.out.printf("%.6f", avg);

        }
    }

![](/img/average_0.PNG)

지금까지 C로만 백준 알고리즘을 풀었는데, 자바로푸니 신세계였다.

우선 input을 받아 배열을 만들었다.
그 이후론 그냥 문제에 나온 대로 구현만 해서 난이도는 매우 쉬웠다. 다만 다른 사람의 깔끔한 풀이를 참고해서, 클린코드를 지향하는것을 목표로 다시 피드백을 해보자.

## 다른 사람의 풀이

    import java.io.BufferedReader;
    import java.io.InputStreamReader;

    public class Main {
        public static void main(String[] args) throws Exception {
            
            BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
            
            final int total = Integer.parseInt(br.readLine());
            final String[] input = br.readLine().split(" ");
            int score = 0;
            int sum = 0;
            int max = 0;
            int i = 0;
            for ( i = 0; i < input.length; i++ ) {
                score = Integer.parseInt(input[i]);
                sum += score;
                max = score > max ? score : max;
            }
            System.out.println(Math.round(sum * 10000.0 / max / total) / 100.0);
        }
    }

![](/img/average_1.PNG)

누군가의 코드이다. 걸린 시간에서 5배의 차이가 난다. 이 코드에서 내가 배울것들을 정리해보았다.

1. 내가 Scanner 반복문을 사용한 것과는 달리, BuferedReader와 InputStreamReader을 사용했다. 입력으로 BufferedReader을 사용하는 것을 시도해보자.

2. String [] input 배열을 br을 사용해서 초기화하는것은 생각도 못했다. 반복문보다 이게 더 깔끔해보인다.




### 태그 : 수학