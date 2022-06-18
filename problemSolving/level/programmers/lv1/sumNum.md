# 없는 숫자 더하기

## 문제

0부터 9까지의 숫자 중 일부가 들어있는 배열 numbers가 매개변수로 주어집니다. numbers에서 찾을 수 없는 0부터 9까지의 숫자를 모두 찾아 더한 수를 return 하도록 solution 함수를 완성해주세요.

## 입출력 예

    numbers	result
    [1,2,3,4,6,7,8,0]	14
    [5,8,4,0,6,7,9]	6


## 코드

    class Solution {

        public static int solution(int[] numbers) {
            int answer = 0;
            int sum = 0;
            for (int i = 0; i < numbers.length ; i ++) {
                sum += numbers[i];
            }
            
            answer = 45 - sum;
            
            return answer;
        }
    }

## 풀이

완전 뒷통수를 제대로 맞은 문제이다.
원래 배열을 2개 만들어서 for문으로 비교해가면서 없는 숫자를 구하고, 더하는 그런 복잡한 형식의 코드를 구성했다.

하지만.. 이렇게 간단하게도 풀수 있는 문제였다.

결론 : 문제를 어떻게 해결할 것인지에 대한 고민을 많이 하자.

![](/img/sumNum_0.PNG)