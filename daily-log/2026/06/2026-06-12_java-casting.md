# 2026-06-12 Java 형변환 정리

## 1. 오늘 공부한 내용

오늘은 Java 입문 강의의 `스코프, 형변환` 단원 중에서 형변환 부분을 공부했다.

이번에 공부한 내용은 다음과 같다.

- 자동 형변환
- 명시적 형변환
- 작은 타입에서 큰 타입으로 대입할 때
- 큰 타입에서 작은 타입으로 대입할 때
- 소수점 버림
- 오버플로우
- 계산할 때의 형변환
- `int / int` 계산 결과
- `double / int` 계산 결과
- 계산 전에 형변환을 해야 하는 이유

형변환은 단순히 타입 이름을 바꾸는 것이 아니라,
값을 다른 타입의 변수에 넣거나 계산할 때 Java가 내부적으로 어떻게 처리하는지 이해하는 내용이었다.

특히 이번 단원에서는 `int`, `long`, `double`의 관계를 중심으로 공부했다.

```java
int < long < double
```

작은 범위에서 큰 범위로 갈 때는 Java가 자동으로 형변환해준다.

하지만 큰 범위에서 작은 범위로 갈 때는 값 손실이 생길 수 있기 때문에 개발자가 직접 명시적 형변환을 해야 한다.

---

## 2. 형변환이란?

형변환은 값의 타입을 다른 타입으로 바꾸는 것이다.

예를 들어 다음과 같은 경우가 형변환이다.

```java
int -> long
int -> double
double -> int
long -> int
```

Java에서 변수는 타입을 가진다.

```java
int a = 10;
double b = 10.0;
```

`a`는 정수를 저장하는 `int` 타입이고,
`b`는 실수를 저장하는 `double` 타입이다.

타입이 다르면 값을 넣거나 계산할 때 Java가 타입을 맞춰야 한다.

이때 타입을 바꾸는 것이 형변환이다.

---

## 3. 숫자 타입의 범위

이번 강의에서는 숫자 타입의 범위를 다음 순서로 이해하면 된다.

```java
int < long < double
```

- `int`는 정수를 저장한다.
- `long`은 `int`보다 더 큰 정수를 저장할 수 있다.
- `double`은 실수까지 저장할 수 있고, 더 넓은 범위를 표현할 수 있다.

작은 범위의 값을 큰 범위에 넣는 것은 문제가 없다.

예를 들어 작은 컵에 있는 물을 큰 컵에 옮기는 것은 넘치지 않는다.

반대로 큰 범위의 값을 작은 범위에 넣으면 문제가 생길 수 있다.

예를 들어 큰 컵에 있는 물을 작은 컵에 옮기면 물이 넘칠 수 있다.

형변환에서 조심해야 하는 문제는 크게 두 가지이다.

1. 소수점 버림
2. 오버플로우

---

## 4. 자동 형변환

자동 형변환은 작은 타입의 값을 큰 타입에 넣을 때 Java가 알아서 타입을 바꿔주는 것이다.

다른 말로는 묵시적 형변환이라고도 한다.

작은 범위에서 큰 범위로 가는 것은 값이 손실될 위험이 적기 때문에 Java가 자동으로 허용한다.

예를 들어 `int` 값을 `long`에 넣거나,
`int` 값을 `double`에 넣는 것은 가능하다.

```java
int -> long
int -> double
long -> double
```

---

## 5. 자동 형변환 예제 코드

```java
package casting;

public class Casting1 {
    public static void main(String[] args) {
        int intValue = 10;
        long longValue;
        double doubleValue;

        longValue = intValue; // int -> long
        System.out.println("longValue = " + longValue);

        doubleValue = intValue; // int -> double
        System.out.println("doubleValue1 = " + doubleValue);

        doubleValue = 20L; // long -> double
        System.out.println("doubleValue2 = " + doubleValue);
    }
}
```

실행 결과는 다음과 같다.

```text
longValue = 10
doubleValue1 = 10.0
doubleValue2 = 20.0
```

---

## 6. int에서 long으로 자동 형변환

```java
int intValue = 10;
long longValue;

longValue = intValue;
```

`intValue`는 `int` 타입이고 값은 10이다.

`longValue`는 `long` 타입이다.

`long`은 `int`보다 더 큰 범위의 정수를 저장할 수 있다.

그래서 `int` 값을 `long` 변수에 넣는 것은 문제가 없다.

Java는 내부적으로 다음처럼 처리한다고 이해하면 된다.

```java
longValue = intValue;
longValue = (long) intValue;
longValue = (long) 10;
longValue = 10L;
```

개발자가 직접 `(long)`이라고 쓰지 않아도 Java가 알아서 바꿔준다.

그래서 이것을 자동 형변환이라고 한다.

---

## 7. int에서 double로 자동 형변환

```java
doubleValue = intValue;
```

`intValue`는 `int` 타입이다.

`doubleValue`는 `double` 타입이다.

`double`은 실수까지 표현할 수 있기 때문에 `int`보다 더 넓은 범위이다.

그래서 `int` 값 10은 `double` 값 10.0으로 자동 변환된다.

처리 과정은 다음과 같다.

```java
doubleValue = intValue;
doubleValue = (double) intValue;
doubleValue = (double) 10;
doubleValue = 10.0;
```

그래서 출력 결과가 다음처럼 나온다.

```text
doubleValue1 = 10.0
```

여기서 중요한 점은 `10`이 `10.0`으로 출력된다는 것이다.

`double`은 실수 타입이기 때문에 정수처럼 보여도 실수 형태로 저장된다.

---

## 8. long에서 double로 자동 형변환

```java
doubleValue = 20L;
```

`20L`은 `long` 타입 리터럴이다.

숫자 뒤에 `L`이 붙으면 `long` 타입이라는 뜻이다.

그런데 `doubleValue`는 `double` 타입이다.

`long`보다 `double`이 더 넓은 범위이기 때문에 자동 형변환이 일어난다.

처리 과정은 다음과 같다.

```java
doubleValue = 20L;
doubleValue = (double) 20L;
doubleValue = 20.0;
```

그래서 결과는 다음처럼 나온다.

```text
doubleValue2 = 20.0
```

---

## 9. 자동 형변환 핵심 정리

자동 형변환은 작은 범위에서 큰 범위로 갈 때 일어난다.

```java
int -> long
int -> double
long -> double
```

이런 변환은 값 손실 위험이 적기 때문에 Java가 자동으로 허용한다.

정리하면 다음과 같다.

```text
작은 타입의 값은 큰 타입 변수에 넣을 수 있다.
이때 Java가 자동으로 타입을 바꿔준다.
이것을 자동 형변환 또는 묵시적 형변환이라고 한다.
```

---

## 10. 명시적 형변환

명시적 형변환은 큰 타입의 값을 작은 타입에 넣을 때 개발자가 직접 타입을 바꿔주는 것이다.

자동 형변환과 반대이다.

큰 타입에서 작은 타입으로 갈 때는 값이 손실될 수 있기 때문에 Java가 자동으로 허용하지 않는다.

예를 들어 `double`은 실수를 저장할 수 있지만,
`int`는 정수만 저장할 수 있다.

그래서 `double` 값 1.5를 `int`에 넣으면 소수점 `.5`를 저장할 수 없다.

이런 경우 Java는 컴파일 오류를 발생시킨다.

---

## 11. double을 int에 바로 넣으면 오류가 난다

예제 코드는 다음과 같다.

```java
package casting;

public class Casting2 {
    public static void main(String[] args) {
        double doubleValue = 1.5;
        int intValue = 0;

        // intValue = doubleValue; // 컴파일 오류 발생

        intValue = (int) doubleValue; // 형변환
        System.out.println(intValue); // 출력: 1
    }
}
```

오류가 나는 코드는 다음 부분이다.

```java
intValue = doubleValue;
```

이 코드는 오류가 난다.

이유는 `doubleValue`는 `double` 타입이고,
`intValue`는 `int` 타입이기 때문이다.

`double`은 `int`보다 더 큰 범위이고 실수도 표현할 수 있다.

그런데 `int`는 소수점을 표현할 수 없다.

그래서 Java는 값 손실이 생길 수 있다고 판단하고 컴파일 오류를 발생시킨다.

오류 메시지는 다음처럼 이해하면 된다.

```text
double을 int로 바꾸면 값 손실이 생길 수 있어서 안 된다.
```

---

## 12. 명시적 형변환 문법

큰 타입에서 작은 타입으로 바꾸고 싶다면 개발자가 직접 괄호를 사용해서 타입을 적어야 한다.

```java
intValue = (int) doubleValue;
```

여기서 `(int)`가 명시적 형변환이다.

처리 과정은 다음과 같다.

```java
intValue = (int) doubleValue;
intValue = (int) 1.5;
intValue = 1;
```

`doubleValue` 안에 있는 값 1.5를 읽고,
그 값을 `int`로 바꾸면서 소수점 아래가 버려진다.

그래서 결과는 1이 된다.

---

## 13. 명시적 형변환을 해도 원래 변수 값이 바뀌는 것은 아니다

여기서 중요한 점이 있다.

```java
intValue = (int) doubleValue;
```

이 코드는 `doubleValue` 자체를 `int`로 바꾸는 것이 아니다.

`doubleValue` 안에 있는 값을 읽어서,
그 값을 잠깐 `int`로 바꾼 다음,
그 결과를 `intValue`에 넣는 것이다.

즉, `doubleValue` 안의 값은 여전히 1.5이다.

변수의 값은 대입 연산자 `=`로 직접 다시 넣을 때만 바뀐다.

정리하면 다음과 같다.

```text
형변환은 원본 변수 자체를 바꾸는 것이 아니다.
변수에서 읽어온 값을 잠깐 다른 타입으로 바꾸는 것이다.
```

이 부분은 처음 공부할 때 헷갈릴 수 있다.

예를 들어 화장품 샘플을 덜어서 다른 통에 담는다고 해서,
원래 본품 용기의 내용물이 갑자기 바뀌는 것은 아닌 것처럼 이해하면 된다.

---

## 14. 명시적 형변환의 위험

명시적 형변환은 개발자가 위험을 감수하겠다는 뜻이다.

Java가 원래 막아주는 이유는 값 손실이 생길 수 있기 때문이다.

예를 들어 다음 코드를 보자.

```java
double doubleValue = 1.5;
int intValue = (int) doubleValue;
```

결과는 다음과 같다.

```text
1
```

`1.5`가 `1`이 되었다.

즉, 소수점 아래 `.5`가 사라졌다.

만약 평균 계산, 돈 계산, 비율 계산 같은 코드에서 이런 일이 생기면 문제가 될 수 있다.

그래서 Java는 큰 타입에서 작은 타입으로 자동 변환을 하지 않는다.

---

## 15. 형변환과 오버플로우

명시적 형변환에서 또 조심해야 하는 것이 오버플로우이다.

오버플로우는 타입이 표현할 수 있는 범위를 넘었을 때 전혀 다른 값이 나오는 현상이다.

예제 코드는 다음과 같다.

```java
package casting;

public class Casting3 {
    public static void main(String[] args) {
        long maxIntValue = 2147483647; // int 최고값
        long maxIntOver = 2147483648L; // int 최고값 + 1

        int intValue = 0;

        intValue = (int) maxIntValue;
        System.out.println("maxIntValue casting=" + intValue);

        intValue = (int) maxIntOver;
        System.out.println("maxIntOver casting=" + intValue);
    }
}
```

실행 결과는 다음과 같다.

```text
maxIntValue casting=2147483647
maxIntOver casting=-2147483648
```

---

## 16. int의 최대값

`int`가 표현할 수 있는 가장 큰 값은 다음과 같다.

```java
2147483647
```

그래서 다음 코드는 문제가 없다.

```java
long maxIntValue = 2147483647;
int intValue = (int) maxIntValue;
```

처리 과정은 다음과 같다.

```java
maxIntValue = 2147483647;
intValue = (int) maxIntValue;
intValue = (int) 2147483647L;
intValue = 2147483647;
```

`2147483647`은 `int` 범위 안에 있으므로,
`long`에서 `int`로 바꿔도 문제가 없다.

---

## 17. int 범위를 넘으면 오버플로우가 발생한다

문제는 다음 값이다.

```java
long maxIntOver = 2147483648L;
```

`2147483648L`은 `int` 최대값인 `2147483647`보다 1 크다.

그래서 `int`로 표현할 수 없다.

그런데 억지로 명시적 형변환을 하면 다음처럼 된다.

```java
intValue = (int) maxIntOver;
```

처리 과정은 다음과 같다.

```java
maxIntOver = 2147483648L;
intValue = (int) maxIntOver;
intValue = (int) 2147483648L;
intValue = -2147483648;
```

결과가 이상하게 `-2147483648`이 된다.

이게 오버플로우이다.

오버플로우는 마치 시계가 한 바퀴 돌아서 다시 처음으로 가는 것처럼,
범위를 넘어가면 예상하지 못한 값이 나오는 현상이다.

---

## 18. 오버플로우에서 중요한 점

오버플로우에서 중요한 것은 결과가 정확히 왜 저 숫자인지 외우는 것이 아니다.

중요한 것은 이것이다.

```text
오버플로우가 발생하면 안 된다.
```

오버플로우가 발생했을 때 결과를 계산하려고 시간을 쓰는 것보다,
처음부터 오버플로우가 발생하지 않게 타입을 크게 잡는 것이 중요하다.

예를 들어 `int`로 부족하면 `long`을 사용하면 된다.

```java
long value = 2147483648L;
```

이렇게 표현할 수 있는 범위가 더 큰 타입을 사용하면 오버플로우 문제를 피할 수 있다.

---

## 19. 계산과 형변환

형변환은 변수에 값을 대입할 때만 일어나는 것이 아니다.

계산할 때도 형변환이 일어난다.

Java에서 계산할 때 기억할 규칙은 2가지이다.

1. 같은 타입끼리 계산하면 같은 타입의 결과가 나온다.
2. 서로 다른 타입끼리 계산하면 더 큰 범위의 타입으로 자동 형변환된다.

예를 들어 `int / int`는 결과도 `int`이다.

반대로 `double / int`는 더 큰 타입인 `double` 기준으로 계산된다.

---

## 20. 같은 타입끼리 계산하면 같은 타입이 나온다

예를 들어 다음 코드를 보자.

```java
int div1 = 3 / 2;
```

`3`도 `int`이고,
`2`도 `int`이다.

즉, `int / int`이다.

같은 `int`끼리 계산했기 때문에 결과도 `int`가 된다.

수학적으로는 1.5가 나와야 할 것 같지만,
`int`는 정수만 저장할 수 있으므로 결과는 1이 된다.

처리 과정은 다음과 같다.

```java
int div1 = 3 / 2;
int div1 = 1;
```

소수점이 버려진다.

---

## 21. double 변수에 넣어도 이미 계산이 끝난 뒤면 1.0이 된다

다음 코드는 처음 보면 헷갈릴 수 있다.

```java
double div2 = 3 / 2;
```

왼쪽은 `double`인데 결과가 1.5가 아니라 1.0이다.

이유는 계산 순서 때문이다.

먼저 오른쪽의 `3 / 2`가 계산된다.

```java
double div2 = 3 / 2;
double div2 = 1;
double div2 = (double) 1;
double div2 = 1.0;
```

`3 / 2`는 `int / int`이므로 먼저 `int` 결과인 1이 나온다.

그 다음 그 결과 1을 `double` 변수에 넣기 위해 1.0으로 자동 형변환한다.

그래서 최종 결과는 1.0이다.

이 부분이 진짜 중요하다.

```text
double 변수에 넣는다고 해서 계산 과정이 처음부터 double이 되는 것은 아니다.
오른쪽 계산이 먼저 끝나고, 그 결과가 왼쪽 변수에 들어간다.
```

---

## 22. 처음부터 double이 섞이면 결과가 double이 된다

다음 코드는 결과가 1.5이다.

```java
double div3 = 3.0 / 2;
```

여기서는 `3.0`이 `double`이다.

그래서 `double / int` 계산이 된다.

서로 다른 타입끼리 계산하면 더 큰 타입으로 자동 형변환된다.

즉, `2`가 `2.0`으로 바뀐다.

처리 과정은 다음과 같다.

```java
double div3 = 3.0 / 2;
double div3 = 3.0 / (double) 2;
double div3 = 3.0 / 2.0;
double div3 = 1.5;
```

그래서 결과가 1.5가 된다.

---

## 23. 명시적 형변환으로 계산 결과를 double로 만들기

`3 / 2`에서 1.5를 얻고 싶다면 둘 중 하나를 `double`로 바꾸면 된다.

```java
double div4 = (double) 3 / 2;
```

처리 과정은 다음과 같다.

```java
double div4 = (double) 3 / 2;
double div4 = 3.0 / 2;
double div4 = 3.0 / (double) 2;
double div4 = 3.0 / 2.0;
double div4 = 1.5;
```

`3`을 먼저 `double`로 바꿨기 때문에,
계산 전체가 `double` 기준으로 진행된다.

그래서 결과가 1.5가 된다.

---

## 24. 변수를 사용할 때도 형변환할 수 있다

숫자를 직접 쓰는 것이 아니라 변수로 계산할 때도 똑같다.

```java
int a = 3;
int b = 2;

double result = (double) a / b;
```

처리 과정은 다음과 같다.

```java
double result = (double) a / b;
double result = (double) 3 / 2;
double result = 3.0 / 2;
double result = 3.0 / 2.0;
double result = 1.5;
```

여기서 중요한 것은 `(double) a`이다.

`a`를 먼저 `double`로 바꿨기 때문에,
`b`도 자동으로 `double`로 바뀌고,
결과도 `double`이 된다.

---

## 25. 계산과 형변환 전체 코드

```java
package casting;

public class Casting4 {
    public static void main(String[] args) {
        int div1 = 3 / 2;
        System.out.println("div1 = " + div1); // 1

        double div2 = 3 / 2;
        System.out.println("div2 = " + div2); // 1.0

        double div3 = 3.0 / 2;
        System.out.println("div3 = " + div3); // 1.5

        double div4 = (double) 3 / 2;
        System.out.println("div4 = " + div4); // 1.5

        int a = 3;
        int b = 2;
        double result = (double) a / b;
        System.out.println("result = " + result); // 1.5
    }
}
```

실행 결과는 다음과 같다.

```text
div1 = 1
div2 = 1.0
div3 = 1.5
div4 = 1.5
result = 1.5
```

---

## 26. 각 결과가 왜 다른지 정리

### div1

```java
int div1 = 3 / 2;
```

`3`과 `2`가 둘 다 `int`이다.

그래서 `int / int` 계산이 된다.

결과도 `int`이므로 1.5가 아니라 1이 나온다.

---

### div2

```java
double div2 = 3 / 2;
```

왼쪽은 `double`이지만,
오른쪽 계산이 먼저다.

오른쪽 `3 / 2`는 `int / int`라서 먼저 1이 된다.

그 다음 1이 `double` 변수에 들어가면서 1.0이 된다.

그래서 결과는 1.0이다.

---

### div3

```java
double div3 = 3.0 / 2;
```

`3.0`이 `double`이다.

그래서 `2`도 자동으로 `double`로 바뀐다.

결국 `3.0 / 2.0`이 되므로 결과는 1.5이다.

---

### div4

```java
double div4 = (double) 3 / 2;
```

`3`을 먼저 `double`로 바꿨다.

그래서 `3.0 / 2`가 되고,
`2`도 자동으로 `2.0`이 된다.

결과는 1.5이다.

---

### result

```java
int a = 3;
int b = 2;
double result = (double) a / b;
```

`a`와 `b`는 둘 다 `int`이다.

그런데 계산 전에 `(double) a`를 했다.

그래서 `a`의 값 3이 `3.0`으로 바뀌고,
`b`도 자동으로 `2.0`으로 바뀐다.

결과는 1.5이다.

---

## 27. 오늘 헷갈리기 쉬운 포인트

### 1. 왼쪽 타입이 double이라고 무조건 결과가 1.5가 되는 것은 아니다

```java
double div2 = 3 / 2;
```

이 코드는 결과가 1.5가 아니라 1.0이다.

이유는 오른쪽 계산이 먼저 끝나기 때문이다.

오른쪽이 `int / int`이면 이미 1이 되어버린다.

그 다음에 `double`로 바뀌어도 1.0일 뿐이다.

---

### 2. 계산을 double로 하고 싶으면 계산 전에 double을 섞어야 한다

```java
double div3 = 3.0 / 2;
double div4 = (double) 3 / 2;
```

이렇게 계산 전에 `double`이 하나라도 있어야 결과가 1.5가 된다.

---

### 3. 명시적 형변환은 원본 변수를 바꾸는 것이 아니다

```java
intValue = (int) doubleValue;
```

이 코드는 `doubleValue` 자체를 바꾸는 것이 아니다.

`doubleValue`의 값을 읽어서 잠깐 `int`로 바꾼 다음,
그 결과를 `intValue`에 넣는 것이다.

---

### 4. 큰 타입에서 작은 타입으로 바꿀 때는 조심해야 한다

```java
double doubleValue = 1.5;
int intValue = (int) doubleValue;
```

이렇게 하면 소수점이 버려진다.

결과는 1이다.

---

### 5. 범위를 넘으면 오버플로우가 발생한다

```java
long maxIntOver = 2147483648L;
int intValue = (int) maxIntOver;
```

이 경우 `int` 범위를 넘어서 이상한 값이 나온다.

결과는 다음과 같다.

```text
-2147483648
```

그래서 값이 커질 수 있다면 처음부터 더 큰 타입을 사용해야 한다.

---

## 28. 형변환 전체 핵심 정리

형변환은 값을 다른 타입으로 바꾸는 것이다.

작은 타입에서 큰 타입으로 갈 때는 자동 형변환이 된다.

```java
int -> long
int -> double
long -> double
```

큰 타입에서 작은 타입으로 갈 때는 명시적 형변환을 해야 한다.

```java
double -> int
long -> int
```

명시적 형변환은 개발자가 직접 괄호로 타입을 적는다.

```java
intValue = (int) doubleValue;
```

하지만 명시적 형변환은 조심해야 한다.

소수점이 버려질 수 있고,
범위를 넘으면 오버플로우가 발생할 수 있다.

계산할 때도 형변환이 중요하다.

```java
int / int -> int
double / int -> double
int / double -> double
double / double -> double
```

특히 다음 코드는 꼭 기억해야 한다.

```java
double div2 = 3 / 2;
```

이 코드는 1.5가 아니라 1.0이다.

오른쪽의 `3 / 2`가 먼저 `int / int`로 계산되어 1이 되기 때문이다.

1.5를 얻고 싶다면 계산 전에 하나를 `double`로 만들어야 한다.

```java
double div3 = 3.0 / 2;
double div4 = (double) 3 / 2;
```

---

## 29. 오늘 공부하면서 이해한 점

오늘 형변환을 공부하면서 중요한 것은 타입이 다르면 Java가 값을 어떻게 처리하는지 보는 것이었다.

처음에는 `double` 변수에 넣으면 당연히 1.5가 나올 것 같았는데,
실제로는 오른쪽 계산이 먼저 끝난다는 점이 중요했다.

```java
double div2 = 3 / 2;
```

이 코드는 왼쪽이 `double`이라서 1.5가 나올 것 같지만,
오른쪽 `3 / 2`가 먼저 `int / int`로 계산되어 1이 된다.

그 다음 1이 `double`에 들어가서 1.0이 된다.

그래서 계산 결과를 실수로 얻고 싶다면,
계산이 시작되기 전에 하나를 `double`로 바꿔야 한다.

```java
double result = (double) a / b;
```

이렇게 하면 `a`가 먼저 `double`이 되고,
전체 계산도 `double` 기준으로 진행된다.

형변환은 단순 문법이 아니라 계산 순서와 타입 범위를 같이 봐야 하는 내용이라는 것을 알게 되었다.

---

## 30. 복학 전 공부 흐름에서의 의미

이번 형변환 공부는 Java 기초 중에서도 중요한 부분이었다.

지금은 휴학 중이고 복학 전까지 전공 기초를 다시 잡는 과정이다.

형변환은 나중에 배열, 메서드, 객체지향, 데이터 처리, 백엔드 공부를 할 때도 계속 나온다.

특히 평균 계산, 비율 계산, 점수 계산, 데이터 변환 같은 코드를 작성할 때
`int`와 `double`의 차이를 제대로 이해하지 못하면 결과가 이상하게 나올 수 있다.

그래서 오늘 공부한 내용은 단순히 문법 하나를 외운 것이 아니라,
Java가 값을 계산하고 저장하는 방식을 이해한 것이라고 생각한다.

앞으로 코드를 볼 때는 다음을 계속 확인해야겠다.

```text
1. 오른쪽 계산이 먼저 실행된다.
2. 같은 타입끼리 계산하면 같은 타입 결과가 나온다.
3. 서로 다른 타입끼리 계산하면 더 큰 타입으로 자동 형변환된다.
4. 큰 타입에서 작은 타입으로 바꾸면 값 손실이 생길 수 있다.
5. 계산 결과를 double로 얻고 싶으면 계산 전에 double을 섞어야 한다.
```

---

## 31. 다음 공부 계획

다음에는 `훈련` 단원이나 `배열` 단원으로 넘어가서,
지금까지 배운 변수, 연산자, 조건문, 반복문, 스코프, 형변환을 직접 코드로 더 많이 연습해야겠다.

특히 단순히 강의를 보는 것에서 끝내지 않고,
직접 코드를 작성하고,
왜 이런 결과가 나오는지 한 줄씩 분석하는 방식으로 공부할 것이다.

지금 공부는 단순히 Java 문법을 외우는 것이 아니라,
복학 전에 전공 기초를 다시 잡고 GitHub에 꾸준히 기록하는 과정이다.

작은 개념이라도 직접 정리하고 기록하면 나중에 객체지향, 백엔드, 앱 개발, 패션 추천 시스템으로 넘어갈 때 기초가 될 것 같다.

## 32. 내가 만들려는 프로젝트와의 연결

내가 최종적으로 만들고 싶은 프로젝트는 패션 추천 시스템이다.

이 시스템은 단순히 옷을 추천하는 것이 아니라,
색상, 핏, 기장, 상황, 분위기 같은 요소를 분석해서 왜 어울리는지 설명하는 방향으로 만들고 싶다.

형변환은 이런 추천 로직을 만들 때도 필요할 수 있다.

예를 들어 옷 조합에 점수를 매긴다고 하면,
색상 점수, 핏 점수, 상황 적합도 점수 등을 숫자로 계산해야 한다.

```java
int colorScore = 80;
int fitScore = 70;
int moodScore = 90;

double average = (double) (colorScore + fitScore + moodScore) / 3;

이때 (double) 형변환을 하지 않으면 평균이 정수로 계산되어 소수점이 사라질 수 있다.

패션 추천 시스템에서는 단순히 “좋다 / 나쁘다”만 판단하는 것이 아니라,
점수나 비율을 계산해서 더 섬세하게 추천해야 할 수도 있다.

예를 들어 다음과 같은 계산이 필요할 수 있다.

색상 조합 점수 평균
전체 코디 균형 점수
어두운 색과 밝은 색의 비율
상황 적합도 점수
추천 우선순위 계산
여러 옷 조합 중 가장 높은 점수 찾기

이런 기능을 만들 때 int와 double의 차이를 모르면 결과가 이상하게 나올 수 있다.

특히 평균이나 비율을 계산할 때는 정수 계산인지 실수 계산인지 꼭 확인해야 한다.

그래서 형변환은 단순 문법이 아니라,
나중에 패션 추천 시스템에서 점수 계산과 추천 로직을 만들기 위한 기초라고 볼 수 있다.

지금은 아주 작은 Java 문법을 공부하고 있지만,
이 개념들이 나중에는 내가 만들고 싶은 추천 시스템의 계산 로직으로 이어질 수 있다고 생각한다.