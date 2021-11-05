# 숫자 문자열과 영단어

## 문제

네오와 프로도가 숫자놀이를 하고 있습니다. 네오가 프로도에게 숫자를 건넬 때 일부 자릿수를 영단어로 바꾼 카드를 건네주면 프로도는 원래 숫자를 찾는 게임입니다.

다음은 숫자의 일부 자릿수를 영단어로 바꾸는 예시입니다.

1478 → "one4seveneight"
234567 → "23four5six7"
10203 → "1zerotwozero3"
이렇게 숫자의 일부 자릿수가 영단어로 바뀌어졌거나, 혹은 바뀌지 않고 그대로인 문자열 s가 매개변수로 주어집니다. s가 의미하는 원래 숫자를 return 하도록 solution 함수를 완성해주세요.

참고로 각 숫자에 대응되는 영단어는 다음 표와 같습니다.

    숫자	영단어
    0	zero
    1	one
    2	two
    3	three
    4	four
    5	five
    6	six
    7	seven
    8	eight
    9	nine

## 제한 사항

1 ≤ s의 길이 ≤ 50
s가 "zero" 또는 "0"으로 시작하는 경우는 주어지지 않습니다.
return 값이 1 이상 2,000,000,000 이하의 정수가 되는 올바른 입력만 s로 주어집니다.

![](/img/stringToInt_0.PNG)

## 코드

    class Solution {
        public int solution(String s) {
        int answer;
            
            String[] num = {"0", "1", "2", "3", "4", "5", "6", "7", "8", "9"};
            String[] word = {"zero", "one", "two", "three", "four", "five", "six", "seven", "eight", "nine"};
            
            for (int i = 0; i<10;  i++) {
                s = s.replace(word[i], num[i]);
            }
            
            answer = Integer.parseInt(s);

            
            return answer;
        }
    }

## 풀이

우선 모든 문자를 숫자로 바꿔야한다. 이를 replace메소드를 통해 해결했다.
이후 String형 s를 int형으로 바꾼 후 answer에 대입했다.

replace 와 replaceAll 의 제대로된 사용법을 알아야겠다.

맨처음 replaceAll 메소드를 사용했는데, replace메소드로 바꾸니 잘 동작했다.

Integer.parseInt의 사용법도 숙련이 필요해 보인다.


![](/img/stringToInt_1.PNG)

