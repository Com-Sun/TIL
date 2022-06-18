# java.lang

유일하게 임포트가 필요 없는 기본 패키지.

## Object

hashCode()

생성된 오브젝트의 일련번호

equals()

## String

replaceAll 

    public String replaceAll(String regex, String replacement)

첫번째인자와 동일한것을 삭제 후 두번째 인자로 대체. 이때 반드시 [] 이걸 사용하자. [regex](https://docs.oracle.com/javase/7/docs/api/index.html) 참조

regex 형식 

    [abc]	a, b, or c (simple class)
    [^abc]	Any character except a, b, or c (negation)
    [a-zA-Z]	a through z or A through Z, inclusive (range)
    [a-d[m-p]]	a through d, or m through p: [a-dm-p] (union)
    [a-z&&[def]]	d, e, or f (intersection)
    [a-z&&[^bc]]	a through z, except for b and c: [ad-z] (subtraction)
    [a-z&&[^m-p]]	a through z, and not m through p: [a-lq-z](subtraction)

toupperCase 

    public String toUpperCase()

대문자로 바꾸기

toLowerCase

    public String toLowerCase()

소문자로 바꾸기



-------------------


배열 합치기

1. System.arraycopy()