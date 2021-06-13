# **코딩도장 책 Unit 10_ 상수 사용하기 (02-22)**

- 리터럴 사용 시 주의:

문자열 -> 큰 따옴표(%s), 문자하나->작은 따옴표(%c)

- 정수 리터럴

구분 | 10진수 | 8진수 | 16진수

|:--:|:--:|:--:|:--:|

서식 지정자(format specifier)|%d|0%o|0x%X

진수 변환

10진수|2진수|8진수|16진수

|:--:|:--:|:--:|:--:|

0|0000|00|0

1|0001|01|1

2|0010|02|2

:|:||:

7|0111|07|7

8|1000|10|8

9|1001|11|9

10|1010|12|A

11|1011|13|B

:|:||:

15|1111|17|F

16|10000|20|10

17|10001|21|11

마크다운 표 가운데 정렬 ==

|:--:|

실수 리터럴(끝에)

float|long double|지수표기

|:--:|:--:|:--:|

f / F|l \ L|e / E

ex)

```

printf(("%f",0.1f), printf("%f",0.1F)

```

## **상수 사용하기**

- ***const 자료형 상수이름 =값;***

Python 과 달리 상수 선언 한번하면 값 바꿀 수 x

```

const int con1=1;

con1=2;

ERROR!!!

```

추가> 자료형 const 상수이름=값; 도 가능

# **Unit 11_ 입력 값을 변수에 저장하기 (02-23)**

1. 정수/실수 입력받기(서식지정자만 바꿔주면 됌.)

****scnaf(서식 지정자, 변수의 주소);****

```

#define _CRT_SECURE_NO_WARNINGS

#include <stdio.h>

int main()

{

int num1;

printf("점수를 입력하세요:");

scanf("%d", &num1);

// 표준 입력을 받아서 그 메모리 주소를 변수에 저장(변수 초기화)

printf("%d\n", num1);

return 0;

}

```

scanf 는 나온지 오래된 함수라 입력값의 길이를 설정할 수가 없어 보안에 취약하므로 #define _CRT....을 써서 보안경고로 인한 컴파일 에러를 방지하는 코드를 써줘야 한다.

2. 문자 입력받기

```

#define _CRT_SECURE_NO_WARNINGS

#include  <stdio.h>

int main()

{

char c1;

printf("문자입력: ");

scanf("%c", &c1);

printf("%c\n", c1);

return 0;

}

```

scanf 함수 대신 getchar 함수나 putchar 함수를 사용해도 문자를 입력받을 수 있다.

```

#include <stdio.h>

int main()

{

char c1=getchar();

printf("c\n", c1);

return 0;

}

```

# **Unit 12_ 덧셈, 뺄셈하기 (02-23)**

파이썬과의 차이점

```

#include <stdio.h>

int main()

{

int num1;

int num2;

num1 = 1 + 2;

num2 = 1 - 2;

printf(num1);

printf(num2);

return 0;

}

```

이러면 출력 안 됨.

무조건 서식 지정자 사용해야.

```

#include <stdio.h>

int main()

{

int num1;

int num2;

num1 = 1 + 2;

num2 = 1 - 2;

printf("%d\n", num1);

printf("%d\n", num2);

return 0;

}

```

# **Unit 13_ 증가, 감소 연산자 사용하기 (02-23)**

변수 ++;  or ++변수; -----> 값을 1 증가시킴

변수 --; or --변수; -----> 값을 1 감소시킴

- ***후위 연산자*** (연산을 나중에 처리한다.)

1. A 변수의 값을 B 변수에 할당

2. B는 그대로 있고 A만 +1(-1)

```

#include <stdio.h>

int main()

{

int num1=2;

int num2;

num2=num1++

printf("%d", num2);

return 0;

}

```

num1은 2, num2는 3

- ***전위 연산자*** (연산을 먼저 처리한다.)

1. A에 +1(-1)

2. A 변수의 값을 B에 할당

```

#include <stdio.h>

int main()

{

int num1=2;

int num2;

num2=++num1

printf("%d", num2);

return 0;

}

```

num1도 3, num2도 3

# **Unit14_ 곱셈,나눗셈하기 (02-24)**

1. python에서 7/2->3.5

c에서 7/2하면 3 나옴

2. C언어에서는 정수끼리 나눗셈을 하면 결과도 정수가 나온다.

(살수끼리 나눗셈을 하면 소수점 이하 자리까지 계산된다.)

3. 정수를 그냥 0으로 나누면 컴파일 에러발생(중단)

0을 변수에 저장해서 0으로 나누면 중단은 되지 않으나 실행창에서 에러 뜸.

but (실수 나눗셈에서) 변수에 0.0을 저장해서 0으로 나누면 실행이 중단되지 않고 inf 무한대가  나온다.(p1336 참고)

```

#include <stdio.h>

int main()

{

float num1=3.0f

float num2=0.0f

float num3;

num3=num1/num2;

printf("%f",num3);

return 0;

}

```

-> inf 출력

<참고>

0/10=0

10/0=ERROR

- ***실수계산에서는 계산결과에서 오차가 발생한다.(코딩도장p1333참고)***

# **Unit 15_나머지 연산하기 (02-24)**

1. 나머지연산(%)은 정수에서만 사용가능. 실수에서는 사용 불가능 (ERROR 발생!. but<math.h> 해더 파일을 사용하면 가능.p197참조)

2. 음수의 나머지 연산.

a/b에서 a의 부호를 따른다.(b 부호는 무시)

# **Unit 16_자료형의 확장과 축소 (02-24)**

## **형 확장**

정수와 실수를 같이 연산하면 출력은 실수형으로 된다. (표현범위가 큰 쪽)

크기가 다른 정수끼리 연산했을때도 마찬가지.

ex)

int(4byte)형과 longlong(8byte)을 같이 썼을 때-> longlong으로 출력.

## **형 축소(값 손실 발생)**

char과 int를 함께 연산한 뒤 char에 저장하면 char 보다 큰 숫자는 저장할 수 없다.

ex)

char=28;

int=100000002;

char이 1byte니까 int형에서 1byte만 유효하고  나머지는 버려진다. (이진수)

100000002(10)->0011 1011 1001 1010 1100 1010 0000 0010(2) 에서 뒤에 1byte인 0000 0010 만 사용.

$$ 마크다운 내부 링크 걸고 싶으면[보여질 글씨](#해더 이름) 쓰면 된다. 해더 이름의 띄어쓰기는'_'로 처리한다.$$

# **Unit17_ if 조건문 (02-25)**

1. 문법

if (조건식)

```

if (num1==10)

{

printf("10입니다.");

}

```

(뒤에 ; 안씀)

만약 if 조건문 끝에 세미콜론이 붙어있으면 if는 제대로 동작하지 않고 뒤에 오는 코드가 무조건 실행되어 버린다.

```

if (num1==10);

printf("10입니다.");

```

if와 printf는 전혀 관계가 없이 떨어진 상태가 됨->조건식이 어떻든 printf는 항상 실행된다.

<span style="color:red">주의</span>

if 뒤에 세미콜론을 붙여도 컴파일 에러가 나지 않기 때문에 문제를 발견하기가 쉽지 않다 조심하자

# Unit 18_else 사용하여 분기하기(02-25)

else도 세미콜론을 붙이지 않는다!!

세미콜론 붙이면 if 의 결과와는 관계없이 항상 실현됨!!!!!

C에서는 0을 거짓, 0이 아닐 때를 참으로 동작함.

```

#include <stdio.h>

int main()

{

if (2)

{

printf("참");

}

else

{

printf("거짓");

}

return 0;

}

```

출력:참

```

#include <stdio.h>

int main()

{

if (0)

{

printf("참");

}

else

{

printf("거짓");

}

return 0;

}

```

출력: 거짓

++ 경고 수준 조정 Wparenthese

(p228 참고)

# **Unit 19_ else if를 사용하여 여러 방향으로 분기 (02-25)**

```

else if (조건식)  //else if에 조건식을 지정하지 않으면 컴파일 에러 발생

```

if 조건문 안에 if 조건문은 63개 까지 중첩할 수 있다.

# **Unit 20_ 비교 연산자와 삼항 연산자 사용**

## **1. 조건부 연산자**

?:

조건식이 참이면 ':'앞의 값을 반환, 거짓이면 ':' 뒤의 값을 반환

ex) x ? a : b

## **2. 비교 연산자**

참이면 1, 거짓이면 0 출력

```

#include <stdio.h>

int main()

{

int num1 = 10;

printf("%d\n", num1 == 10);

printf("%d\n", num1 != 10);

return 0;

}

```

한 숫자만 not 연산하기

```

if (!num1)

printf("참");

```

## **3. 삼항 연산자**

```c
#include <stdio.h>

int main()

{

int num1=5;

int num2;

if (num1)

num2=100;

else

num2=200;

printf("%d\n", num2);

return 0;

}
```

```

출력:100

num1에 저장된 5는 0이 아닌 값이므로 참이다. 따라서 num2에는 100이 할당 됨.

```c
#include <stdio.h>

int main()

{

int num1=5;

int num2;

num2=num1 ? 100 : 200;

//num1이 참이면(0이 아니면) num2=100, num1이 거짓이면(0이면) num2=200

printf("%d\n", num2);

return 0;

}
```

```

- -->삼항 연산자는 if , else로 분기하는 부분을 한 줄로 간단하게 줄일 수 있다.

```

num2=(num1==10) ? 100 : 200;

```

과 같이 쓸수도 있다. num1==10일때는 num2=100.

# **Unit 21_ 논리 연산자**

연산자|설명

|:--:|:--:|

&&|AND

kk|OR

!|NOT

(k==|)

1. &&은 두 값이 모두 참이라야 결과가 참.

- 2&&0 이면 거짓임(0 있으니까)
- 2&&3은 참임( 0없으니까)

2. ||은 두 값 중 하나만 참이라도 결과가 참이 나옴.

0||0만 거짓임. 0출력

```

printf(~~~~

"%d",!1  // 원래의 반대.1은 참인데 !1이니까 거짓임->0출력

"%d",!0  // 0은 거짓인데 !0이니까 참-> 1출력

"%d",!3 // 3은 참인데 !3이니까 거짓->0출력

```

# **Unit 22_불 자료형**

1. <stdbool.h> 해더 파일 이용.

- bool, true, false 가 저장 되어 있음.
- 0은 거짓, 0아니면 참으로 했지만 이 해더파일 사용하면 true를 참으로 false를 거짓으로 나타낼 수 있다.

```

if (b1==true)

printf("참");

```

- 하지만 출력할 때는 정수 출력처럼 %d 사용한다.

```

printf("%d", true&&true);

```

2. 1byte 임  **(int는 4byte)**

3. 전용 서식  지정자 x.

++삼항 연산자는 조건식 뿐만아니라 참, 거짓 값으로도 판단할 수 o

```

#include <stdio.h>

#include <stdbool.h>

int main()

{

bool b1 = true;

printf(b1 ? "true" : "faflse");

return 0;

}

```

- ->출력: true

다른 자료형은 해더파일 없이 사용할 수 있는데 bool은 해더 파일을 포함하는 이유?

char, int등의 자료형은 C언어가 나올 때부터 있었지만 bool은 나중에 추가된 자료형이기 때문이다.

해더 파일 없이 불 자료형을 사용하려면 _Bool로 선언해야 한다.
