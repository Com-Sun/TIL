# switch 문 사용법

switch문은 쉽게 생각하면 if문과 비슷하다.
단순하게 if else와 비교해서 보기 쉽다는 장점이 있다.

## if 문의 경우

    int a;
    scanf("%d", &a);

    if (a == 1)
    {
        printf("a는 1입니다.");
    }

    else if (a == 2)
    {
        printf("a는 2입니다.");
    }

    else
    {
        printf("이해하지 못했습니다.");
    }

## switch 문의 경우

    int a;
    scanf("%d", &a);

    switch (a) {
    case 1:
        printf("a 는 1입니다.");
        break;

    case 2:
        printf("a 는 2입니다.");
        break;

    default:
        printf("무슨 말인지 이해하지 못했습니다.");
        break;
    }

case 구분에는 반드시 정수가 들어가야한다. int, char, short, long을 제외한 float, double은 사용하지 못한다. 또한, 변수도 사용할 수 없다.

# switch 문과 if else 문의 본질적인 차이점

이 둘은 내부적으로 처리되는 과정에서 차이를 보인다.
본질적인 차이를 구분하는 것은 아직 내 수준에서는 무리이고, 러프한 수준에서 비교하자면

    속도에서 차이가 난다.

else if의 경우 모든 케이스를 비교한다. (어셈블리어에선 CMP연산.)
반면에 switch는 jump table을 생성하여 해당 case로 점프한다. (성능에 영향 X)

추가적으로 jump table은 프로그램이 시작되기 전에 생성된다. 위에서 서술한 '값'부분에 변수가 올 수 없는 이유이다.
