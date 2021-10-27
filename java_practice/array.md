배열을 생성할 때 초기값이 주어지면 배열의 크기를 지정할 수 없다.

    int [] jumsu = new int [] {1, 2, 3};

위에서 뒤의 []안에 3이 들어가면 안된다.

반복문에서 C언어와는 다르게, 길이를 알려주는 함수 length를 사용하면 for문에서 편하다.

예시)

	for (int i = 0; i <num.length; i ++) {
		sum += num[i];
	}

---
int [] a = new int [3];
long [] b = new long [3];

출력은 다 0이지만, 데이터 타입은 위에선 int이고 아래는 0L 이다!!!


궁금한점 : 		int arr[] = new int[3];

위의 코드와

int arr[] = {1,2,3} 이것의 차이는 무엇일까

---
num.length : 행의 길이

num[행인덱스].length : 행인덱스에 대한 열의 크기


---
배열 생성과 동시에 초기화를 하고싶다면 ?

    int [][] arr = new int [][] { {1,2}, {3,4}, {5,6} };

---

이차원 배열에 관한 개념. C언어랑 상당히 비슷한듯.

row : arr.length
col : arr[row].length

이차원배열에서 열의 길이는 가변적으로 설정 가능