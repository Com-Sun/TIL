## 문제

세 개의 자연수 A, B, C가 주어질 때 A × B × C를 계산한 결과에 0부터 9까지 각각의 숫자가 몇 번씩 쓰였는지를 구하는 프로그램을 작성하시오.

예를 들어 A = 150, B = 266, C = 427 이라면 A × B × C = 150 × 266 × 427 = 17037300 이 되고, 계산한 결과 17037300 에는 0이 3번, 1이 1번, 3이 2번, 7이 2번 쓰였다.

## 입력

첫째 줄에 A, 둘째 줄에 B, 셋째 줄에 C가 주어진다. A, B, C는 모두 100보다 크거나 같고, 1,000보다 작은 자연수이다.

## 출력

첫째 줄에는 A × B × C의 결과에 0 이 몇 번 쓰였는지 출력한다. 마찬가지로 둘째 줄부터 열 번째 줄까지 A × B × C의 결과에 1부터 9까지의 숫자가 각각 몇 번 쓰였는지 차례로 한 줄에 하나씩 출력한다.

## 풀이

    int arr[10];
    int input_arr[3];
    int input;
    int i;

    for (i = 0; i < 3; i++) {
        scanf("%d", &input);
        input_arr[i] = input;
    }

    for (i = 0; i < 3; i++) {
        printf("%d\n", input_arr[i]);
    }

조건을 확인해보니 나올수 있는 수는 최대 10^9이다. 이 수를 넣어줄 배열 arr을 만들었다.
그 후에 A,B,C의 값을 넣어줄 배열 input_arr을 만든 뒤 오류가 없는지 printf로 출력해보았다.

![](/img/num_count_0.PNG)

잘 만들어진것을 확인했으니 input_arr의 각 요소를 곱하고, 새 변수 multiplied_abc에 대입해준다.

    for (i = 0; i < 3; i++) {
            multiplied_abc *= input_arr[i];
        }

    printf("%d\n", multiplied_abc);

![](/img/num_count_1.PNG)

잘 작동한다.
곱해진 수 abc의 각 자릿수를 배열 arr에 잘 집어넣어야 할 차례다.

    162 / 1 % 10
    162 / 10 % 10
    162 / 100 % 10

위와같이 코드를 짜면 될 것 같다.

_디버깅을 하던 와중 C에서 10^i 가 불가능하다는 것을 깨달았다._

    for (i = 9; i >= 0 ; i--) {
            for (j ; j < 1000000001; ) {
                arr[i] = ((multiplied_abc / j) % 10);
                j *= 10;
                break;
            }
        }


        for (i = 0; i < 10; i++) {
            printf("%d", arr[i]);
        }

어쩔수 없이 이중 for문으로 완성한 코드.

![](/img/num_count_2.PNG)

이제 남은 것은 arr에 저장된 각 수만 잘 세는 것 뿐이다.
arr[0] 부터 arr[2] 까지 자리수에 0은 무시하면서 수를 세는 코드를 만들어보자.

#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

    int main() {

        int arr[10];
        int input_arr[3];
        int input;
        int i;
        int j = 1;
        int multiplied_abc = 1;
        int fin[10];
        int count;

        for (i = 0; i < 3; i++) {
            scanf("%d", &input);
            input_arr[i] = input;
        }

        for (i = 0; i < 3; i++) {
            multiplied_abc *= input_arr[i];
        }


        for (i = 9; i >= 0; i--) {
            for (j; j < 2000000001; j *= 10) {
                arr[i] = ((multiplied_abc / j) % 10);
                j *= 10;
                break;
            }
        }

        for (i = 0; i < 10; i++) {
            count = 0;
            for (int k = 0; k < 10; k++) {
                fin[i] = count;

                if (i == arr[k]) {
                    count++;
                    fin[i] = count;
                }

            }
        }

        int* parr = fin;
        int count_2 = 0;
        for (int i = 1; i < 3; i++) {
            if (arr[i] != 0) {
                break;
            }

            else if (arr[i] == 0) {
                count_2++;
            }
        }

        parr[0] -= (count_2 + 1);


        for (i = 0; i < 10; i++) {
            printf("%d\n", parr[i]);
        }

        return 0;
    }

![](/img/num_count_3.PNG)

피드백 : 

    #include <stdio.h>

    int main(void)
    {
        int a, b, c;
        scanf("%d\n%d\n%d", &a, &b, &c);
        int weight[10] = {0, };
        long temp = a * b * c;
        while (temp > 0)
        {
            weight[temp % 10]++;
            temp /= 10;
        }

        for (int i = 0; i < 10; i++)
            printf("%d\n", weight[i]);

        return 0;
    }

이렇게 간단하게 풀 수도 있는 문제였다.. 허허
