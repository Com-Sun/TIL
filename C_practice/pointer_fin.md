# 포인터 씹어먹기

이 문서는 comp.lang.c의 공식 [FAQ](http://www.c-faq.com/index.html)와, 이를 번역하신 신성국님의 [온라인 문서](https://cinsk.github.io//ko/cfaqs/index.html)를 참고하였습니다.

모든 내용은 C99에 해당하는 레퍼런스를 가집니다.

# 배열과 포인터

    A strength of C is its unification of arrays and pointers. 
    Pointers can be conveniently used to access arrays and to simulate dynamically allocated arrays. 
    The so-called equivalence between arrays and pointers is so close, however,
    that programmers sometimes lose sight of the remaining essential differences between the two,
    imagining either that they are identical or that various nonsensical similarities of identities can be assumed between them.

C의 강점은 배열과 pointer의 유사성이다. 포인터를 통해 배열에 편리하게 접근하고, 동적으로 할당된 어레이를 simulate 할 수 있다. 그러나 포인터와 배열의, 소위 'equivalence'함이 너무나 가까운 나머지 둘 사이에 분명한 차이가 있음에도 불구하고 **동등**하다고 착각한다.

    The cornerstone of the “equivalence” of arrays and pointers in C is the fact that most array references decay into pointers to the array's first element as described in question [*]6.3. 
    Therefore, arrays are “second-class citizens” in C: You can never manipulate an array in its entirely (i.e., to copy it or pass it to a function),
    because whenever you mention its name, you're left with a pointer rather than the entire array.
    Because arrays deacy to pointers, the array subscripting operator [] always find itself, deep down, operating on a pointer.
    In fact, the subscripting expression a[i] is defined in terms of the equivalent pointer expression *((a) + (i)).

C에서 배열과 포인터가 "equivalence"한 것은, 대부분의 배열 reference가 배열의 첫번째 요소를 가리키는 포인터로 '퇴화'되는것에 기초한다. 따라서, C에서 배열은 **2등 시민**이다.
배열 이름 그 자체를 사용할 때 배열 전체가 사용되는것이 아닌 포인터가 남게 된다. 따라서, 당신은 배열 그 자체만을 복사하거나 함수에 전달하는 식의 사용은 불가능하다. 배열이 포인터로 퇴화(decay)되기에, []연산자는  항상 포인터에서 동작한다. 실제로 첨자표현식 a[i]는 포인터표현식*((a) + (i))로 정의된다. 

위 내용은 [pointer_1](./pointer_1.md) 문서에서 간단하게 다루었다. 다시 한 번 확인해보자.

![](/img/function_13.PNG)

이제서야 위의 내용이 제대로 이해가 가는 기분이다.

