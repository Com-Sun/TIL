# 나머지 한 점

## 문제

직사각형을 만드는 데 필요한 4개의 점 중 3개의 좌표가 주어질 때, 나머지 한 점의 좌표를 구하려고 합니다. 점 3개의 좌표가 들어있는 배열 v가 매개변수로 주어질 때, 직사각형을 만드는 데 필요한 나머지 한 점의 좌표를 return 하도록 solution 함수를 완성해주세요. 단, 직사각형의 각 변은 x축, y축에 평행하며, 반드시 직사각형을 만들 수 있는 경우만 입력으로 주어집니다.

## 제한사항

v는 세 점의 좌표가 들어있는 2차원 배열입니다.
v의 각 원소는 점의 좌표를 나타내며, 좌표는 [x축 좌표, y축 좌표] 순으로 주어집니다.
좌표값은 1 이상 10억 이하의 자연수입니다.
직사각형을 만드는 데 필요한 나머지 한 점의 좌표를 [x축 좌표, y축 좌표] 순으로 담아 return 해주세요.

##  입출력 예

입출력 예 #1
세 점이 [1, 4], [3, 4], [3, 10] 위치에 있을 때, [1, 10]에 점이 위치하면 직사각형이 됩니다.

입출력 예 #2
세 점이 [1, 1], [2, 2], [1, 2] 위치에 있을 때, [2, 1]에 점이 위치하면 직사각형이 됩니다

## 코드

    class Solution {
        public int[] solution(int[][] v) {
            int[][] arr = v;
            int[] answer = new int[2];
            int[] answer_1 = new int [3];
            int[] answer_2 = new int [3];

            for (int i = 0; i < 3; i++) {
                answer_1[i] = arr[i][0];
            }


            int a;
            int b;
            int c;
            
            a = answer_1[0];
            b = answer_1[1];
            c = answer_1[2];
            
            if (a != b && a != c) {
                answer[0] = a;
            }
            
            else if (b != a && b!= c) {
                answer[0] = b;
            }
            
            else {
                answer[0] = c;
            }

            for (int i = 0; i < 3; i++) {
                answer_2[i] = arr[i][1];
            }
            
            a = answer_2[0];
            b = answer_2[1];
            c = answer_2[2];
            
            if (a != b && a != c) {
                answer[1] = a;
            }
            
            else if (b != a && b!= c) {
                answer[1] = b;
            }
            
            else {
                answer[1] = c;
            }
            // 행의 첫번째만 비교 : [i],[0] for 연산.
            // 새로운 배열에 저장. 같으면 없애서 answer 0번째에 저장.
            // 행의 두번째만 비교: [i],[1] for 연산
            // 위와 같이.
            // answer리턴
            
            for(int i = 0; i <2; i ++) {
                System.out.println(answer[i]);
            }

            return answer;
        }

        }

문제를 풀면서 느꼈다. 공부할 것이 산더미라는 것을..
우선 나는 문제의 조건과, 해결 방안은 차례대로 구성했다.

주어지는 매개변수는 [3][2] 배열이다. 각 행의 0,1인덱스를 각각 비교한 뒤, 일치하지 않는 수를 answer에 넣어주면 된다. 나는 방법을 몰라 무식하게 a,b,c 변수를 만들고 각각을 비교했다. 문제는 맞았다. 이젠 제대로 된 풀이를 보자.
![](/img/rectangle_0.PNG)

## 풀이

풀이과정에서 벡터가 나온다.. 자바에서 벡터는 아직 진도를 안 나가서 그대로 풀기엔 무리가 있다. 대신 다른 사람이 깔끔하게 푼 풀이를 첨부했다.

[벡터를 이용한 풀이](https://programmers.co.kr/learn/courses/18)


    class Solution {
        public int[] solution(int[][] v) {
            int x;
            int y;

            if(v[0][0]==v[2][0]){
                x=v[1][0];
            }else if(v[1][0]==v[2][0]){
                x=v[0][0];
            }else{
                x=v[2][0];
            }
        
            if(v[0][1]==v[1][1]){
                y=v[2][1];
            }else if(v[1][1]==v[2][1]){
                y=v[0][1];
            }else{
                y=v[1][1];
            }

            int[] answer = {x,y};
            return answer;
        }
    } 

[다른사람의 풀이 출처](https://easy-h.tistory.com/8)

해설 : 내가 a,b,c 를 만들며 구현한 것을 그냥 v[][]를 통해 간단히 구현했다.

(0,0)과 (2,0)이 같을경우 (1,0)을 ans에대입. 아닐경우 조건문을 통해 반복.
