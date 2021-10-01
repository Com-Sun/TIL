## 문제

두 자연수 A와 B가 있을 때, A%B는 A를 B로 나눈 나머지 이다. 예를 들어, 7, 14, 27, 38을 3으로 나눈 나머지는 1, 2, 0, 2이다.

수 10개를 입력받은 뒤, 이를 42로 나눈 나머지를 구한다. 그 다음 서로 다른 값이 몇 개 있는지 출력하는 프로그램을 작성하시오.

## 입력

첫째 줄부터 열번째 줄 까지 숫자가 한 줄에 하나씩 주어진다. 이 숫자는 1,000보다 작거나 같고, 음이 아닌 정수이다.

## 출력

첫째 줄에, 42로 나누었을 때, 서로 다른 나머지가 몇 개 있는지 출력한다.

## 풀이

    #define _CRT_SECURE_NO_WARNINGS
    #include <stdio.h>

    int main() {
        int arr[10] = { 0 };
        int new_arr[42] = { 0 };
        int sum = 0;

        for (int i = 0; i < 10; i++) {
            scanf("%d", &arr[i]);
        }

        for (int i = 0; i < 10; i++) {
            arr[i] = arr[i] % 42;
        }

        for (int i = 0; i < 10; i++) {
            for (int j = 0; j < 42; j++) {
                if (arr[i] == j) {
                    new_arr[j]++;
                }
            }
        }
        /* arr배열 확인
        for (int i = 0; i < 10; i++) {
            printf("%d\n", arr[i]);
        }
        */

        for (int j = 0; j < 42; j++) {
            if (new_arr[j] == 0) {
                sum++;
            }
        }


        //new_arr 확인
        /*
        for (int j = 0; j < 42; j++) {
            printf("%d ", new_arr[j]);
        }

        printf("\n");
        printf("%d", sum);
        */

        printf("%d", 42 - sum);


        return 0;
    }

처음엔 이중 for문을 사용해서 sum++하는 방식으로 코드를 구현했다.
하지만 그 코드는 이중으로 sum을 계산하는 버그가 있었고, 결국 위와 같은 방식으로 문제를 풀 수 있었다.

우선 두개의 크기가 다른 배열 arr, new_arr를 정의하고, 각 원소를 0을 할당했다.

배열 arr에는 42로 나눈 나머지가 들어갔다.

    for (int i = 0; i < 10; i++) {
                arr[i] = arr[i] % 42;
            }

new_arr에는 각 원소의 나머지가 몇 번이나 중복했는지 알 수 있도록 코드를 짰다.

    for (int i = 0; i < 10; i++) {
                for (int j = 0; j < 42; j++) {
                    if (arr[i] == j) {
                        new_arr[j]++;
                    }
                }
            }

마지막으로 new_arr의 원소를 살펴보면, 0의 갯수에 따라 중복된 숫자의 갯수가 달라진다.
하나도 중복된 수가 없을 경우 sum의 숫자는 32.
모두가 중복됐을 경우 sum의 숫자는 41이다.

new_arr의 원소갯수 42에서 sum의 숫자를 빼면 서로 다른 나머지의 갯수를 알 수 있다.

![](/img/rest.PNG)
