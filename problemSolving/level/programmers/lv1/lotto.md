# 로또의 최고 순위와 최저 순위

## 문제

![](/img/lotto_0.PNG)

## 코드

    class Solution {
        public int[] solution(int[] lottos, int[] win_nums) {

            int count = 0;
            int numZero = 0;
            int[] answer = new int[2];

            for (int i = 0; i < 6; i++) {
                if (lottos[i] == 0) {
                    numZero++;
                }
            }

            switch (numZero) {

            case 0:
                for (int i = 0; i < 6; i++) {
                    for (int j = 0; j < 6; j++) {
                        if (lottos[i] == win_nums[j]) {
                            count++;
                        }
                    }
                }
                answer[0] = 7 - count;
                answer[1] = 7 - count;

                if (answer[0] == 7) {
                    answer[0] = 6;
                }

                if (answer[1] == 7) {
                    answer[1] = 6;
                }

                break;

            case 1:
                for (int i = 0; i < 6; i++) {
                    for (int j = 0; j < 6; j++) {
                        if (lottos[i] == win_nums[j]) {
                            count++;
                        }
                    }
                }
                answer[0] = 6 - count;
                answer[1] = 7 - count;

                if (answer[1] == 7) {
                    answer[1] = 6;
                }

                break;

            case 2:
                for (int i = 0; i < 6; i++) {
                    for (int j = 0; j < 6; j++) {
                        if (lottos[i] == win_nums[j]) {
                            count++;
                        }
                    }

                }
                answer[0] = 5 - count;
                answer[1] = 7 - count;

                if (answer[1] == 7) {
                    answer[1] = 6;
                }

                break;

            case 3:
                for (int i = 0; i < 6; i++) {
                    for (int j = 0; j < 6; j++) {
                        if (lottos[i] == win_nums[j]) {
                            count++;
                        }
                    }
                }
                answer[0] = 4 - count;
                answer[1] = 7 - count;

                if (answer[1] == 7) {
                    answer[1] = 6;
                }

                break;

            case 4:
                for (int i = 0; i < 6; i++) {
                    for (int j = 0; j < 6; j++) {
                        if (lottos[i] == win_nums[j]) {
                            count++;
                        }
                    }
                }
                answer[0] = 3 - count;
                answer[1] = 7 - count;

                if (answer[1] == 7) {
                    answer[1] = 6;
                }
                break;

            case 5:
                for (int i = 0; i < 6; i++) {
                    for (int j = 0; j < 6; j++) {
                        if (lottos[i] == win_nums[j]) {
                            count++;
                        }
                    }
                }
                answer[0] = 2 - count;
                answer[1] = 7 - count;

                if (answer[1] == 7) {
                    answer[1] = 6;
                }
                break;

            case 6:
                for (int i = 0; i < 6; i++) {
                    for (int j = 0; j < 6; j++) {
                        if (lottos[i] == win_nums[j]) {
                            count++;
                        }
                    }
                }
                answer[0] = 1 - count;
                answer[1] = 7 - count;

                if (answer[1] == 7) {
                    answer[1] = 6;
                }
                break;
            }

            return answer;
        }
    }


## 풀이

이 문제의 흐름을 살펴보자.

매개변수로 lottos와 win_nums가 주어진다.

1. 0의 갯수 확인

2. lottos == win_nums 인지 확인

3. 0의 갯수와 같은 번호의 갯수에 따라 return값 출력

나는 위와 같이 해결 방법을 구성했다. 그래서 가장 처음 count와 numZero라는 변수를 선언한 뒤, 반복문으로 0의 갯수를 구했다. 다음, switch문을 사용하여 0의 갯수에 따라 케이스를 구분했다.

다음은 매개변수의 각 자릿수가 같은지 확인하는 것을 이차원 배열로 만들었고, 최종값을 answer 배열에 대입했다.

![](/img/lotto_1.PNG)