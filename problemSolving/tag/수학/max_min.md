## 문제

N개의 정수가 주어진다. 이때, 최솟값과 최댓값을 구하는 프로그램을 작성하시오.

## 입력

첫째 줄에 정수의 개수 N (1 ≤ N ≤ 1,000,000)이 주어진다. 둘째 줄에는 N개의 정수를 공백으로 구분해서 주어진다. 모든 정수는 -1,000,000보다 크거나 같고, 1,000,000보다 작거나 같은 정수이다.

## 출력

첫째 줄에 주어진 정수 N개의 최솟값과 최댓값을 공백으로 구분해 출력한다.

---

## 코드

    #define _CRT_SECURE_NO_WARNINGS
    #include <stdio.h>
    #include <stdlib.h>

    int main()
    {
        int size;
        int num;
        int max = -1000000;
        int min = 1000000;
        scanf("%d", &size);


        int* numPtr = malloc(sizeof(int) * size);

        for (int i = 0; i < size; i++)
        {
            scanf("%d", &num);
            numPtr[i] = num;
        }

        for (int i = 0; i < size; i++)
        {
            if (numPtr[i] > max)
            {
                max = numPtr[i];
            }

            if (numPtr[i] < min)
            {
                min = numPtr[i];
            }

        }


        printf("%d %d", min, max);

        return 0;
    }

![](/img/max_min.PNG)

## 풀이

정수의 개수 n을 변수 size에 저장.
동적 할당으로 size크기만큼의 배열을 만든다.
반복문을 통해 max, min 변수에 배열의 i번째 원소와 비교한 값을 할당한다.

### TAG : 수학, 구현
