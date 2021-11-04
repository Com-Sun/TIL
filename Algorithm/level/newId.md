# 신규 아이디 추천

## 문제

![](/img/newId_0.PNG)

    예를 들어, new_id 값이 "...!@BaT#*..y.abcdefghijklm" 라면, 위 7단계를 거치고 나면 new_id는 아래와 같이 변경됩니다.

    1단계 대문자 'B'와 'T'가 소문자 'b'와 't'로 바뀌었습니다.
    "...!@BaT#*..y.abcdefghijklm" → "...!@bat#*..y.abcdefghijklm"

    2단계 '!', '@', '#', '*' 문자가 제거되었습니다.
    "...!@bat#*..y.abcdefghijklm" → "...bat..y.abcdefghijklm"

    3단계 '...'와 '..' 가 '.'로 바뀌었습니다.
    "...bat..y.abcdefghijklm" → ".bat.y.abcdefghijklm"

    4단계 아이디의 처음에 위치한 '.'가 제거되었습니다.
    ".bat.y.abcdefghijklm" → "bat.y.abcdefghijklm"

    5단계 아이디가 빈 문자열이 아니므로 변화가 없습니다.
    "bat.y.abcdefghijklm" → "bat.y.abcdefghijklm"

    6단계 아이디의 길이가 16자 이상이므로, 처음 15자를 제외한 나머지 문자들이 제거되었습니다.
    "bat.y.abcdefghijklm" → "bat.y.abcdefghi"

    7단계 아이디의 길이가 2자 이하가 아니므로 변화가 없습니다.
    "bat.y.abcdefghi" → "bat.y.abcdefghi"

    따라서 신규 유저가 입력한 new_id가 "...!@BaT#*..y.abcdefghijklm"일 때, 네오의 프로그램이 추천하는 새로운 아이디는 "bat.y.abcdefghi" 입니다.

![](/img/newId_1.PNG)
![](/img/newId_2.PNG)

## 풀이

    class Solution {
        public String solution(String new_id) {
            
            String answer = new_id.toLowerCase();
            answer = answer.replaceAll("[^a-z0-9-_.]","");
            answer = answer.replaceAll("[.]{2,}",".");
            answer = answer.replaceAll("^[.]|[.]$", "");
            
            
            if(answer.isEmpty()) {
                answer += "a";
            }
            
            
            if(answer.length() >15) {
                answer = answer.substring(0, 15);
                answer = answer.replaceAll("^[.]|[.]$", "");
            }
            
            
            if(answer.length() < 3) {
                while(answer.length() < 3) {
                    answer += answer.charAt(answer.length()-1);
                }
            }
            
            return answer;
        }
    }

C로 문제를 풀다가 자바로 문제를 푸니 신세계였다.
조건에 맞추어 알맞은 API를 찾아보는것이 관건이었다

문제를 풀며 중요하다고 느낀 메소드

1. replaceAll();

2. substring();

3. charAt();

4. length();

## 결과

![](/img/newId_3.PNG)