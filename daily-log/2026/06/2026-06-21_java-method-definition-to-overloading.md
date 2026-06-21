# 2026-06-21 Java 메서드 정의부터 메서드 오버로딩까지 정리

## 1. 오늘 공부한 내용

오늘은 Java 입문 강의의 `메서드` 단원에서 `메서드 정의`부터 `메서드 오버로딩`까지 공부했다.

이번 정리 범위는 다음과 같다.

* 메서드 정의
* 제어자
* 반환 타입
* 메서드 이름
* 매개변수
* 메서드 본문
* 매개변수가 없는 메서드
* 반환 타입이 없는 메서드
* `void`
* `return`
* 메서드 호출과 값 전달
* 메서드 호출식과 반환값
* 메서드와 형변환
* 메서드 오버로딩
* 메서드 시그니처

이번 범위에서 중요한 것은 메서드를 어떻게 정의하는지,
메서드가 값을 어떻게 받고 돌려주는지,
그리고 같은 이름의 메서드를 여러 개 만들 수 있는 조건이 무엇인지 이해하는 것이다.

---

## 2. 메서드 정의

메서드는 다음과 같은 형태로 정의한다.

```java
public static int add(int a, int b) {
    // 메서드 본문, 실행 코드
}
```

메서드 정의의 기본 구조는 다음과 같다.

```java
제어자 반환타입 메서드이름(매개변수 목록) {
    메서드 본문
}
```

예를 들어 다음 메서드를 보자.

```java
public static int add(int a, int b) {
    int sum = a + b;
    return sum;
}
```

이 메서드는 정수 2개를 받아서 더한 다음,
그 결과를 다시 돌려주는 메서드이다.

---

## 3. 메서드 정의 구조 나누기

```java
public static int add(int a, int b) {
    int sum = a + b;
    return sum;
}
```

이 코드는 다음 부분으로 나눌 수 있다.

```text
public static
→ 제어자

int
→ 반환 타입

add
→ 메서드 이름

int a, int b
→ 매개변수 목록

{
    int sum = a + b;
    return sum;
}
→ 메서드 본문
```

즉, 메서드를 정의할 때는 다음을 생각해야 한다.

```text
1. 이 메서드가 어떤 기능을 할 것인가?
2. 외부에서 값을 받아야 하는가?
3. 값을 받는다면 어떤 타입으로 받을 것인가?
4. 실행 후 결과를 돌려줘야 하는가?
5. 결과를 돌려준다면 어떤 타입으로 돌려줄 것인가?
6. 메서드 이름을 무엇으로 정할 것인가?
```

---

## 4. 제어자

```java
public static
```

이 부분을 제어자라고 한다.

지금 입문 단계에서는 `public`과 `static`의 자세한 의미를 깊게 이해하지 않아도 된다.

현재는 메서드를 만들 때 다음처럼 작성한다고 생각하면 된다.

```java
public static
```

나중에 객체지향을 배우면 `public`, `static`의 의미를 더 자세히 배우게 된다.

지금은 다음 정도로 정리한다.

```text
public static
→ 지금 단계에서는 메서드를 만들 때 붙이는 기본 형식으로 생각한다.
```

---

## 5. 반환 타입

```java
public static int add(int a, int b)
```

여기서 `int`는 반환 타입이다.

반환 타입은 메서드가 실행된 후 호출한 곳으로 돌려주는 값의 타입을 의미한다.

```java
public static int add(int a, int b) {
    int sum = a + b;
    return sum;
}
```

이 메서드는 `sum`을 반환한다.

`sum`은 `int` 타입이다.

그래서 메서드 앞의 반환 타입도 `int`이다.

```text
반환 타입 int
→ 이 메서드는 int 값을 돌려준다.
```

반환 타입이 `int`라면 반드시 `int` 값을 반환해야 한다.

```java
return sum;
```

---

## 6. 메서드 이름

```java
add
```

`add`는 메서드 이름이다.

메서드 이름은 메서드를 호출할 때 사용한다.

```java
add(1, 2);
add(10, 20);
```

메서드 이름은 보통 그 메서드가 하는 일을 알 수 있게 짓는다.

```text
add
→ 더하다
→ 두 숫자를 더하는 메서드
```

메서드 이름을 잘 지으면 코드를 읽을 때 이 메서드가 무슨 일을 하는지 쉽게 알 수 있다.

---

## 7. 매개변수

```java
public static int add(int a, int b)
```

괄호 안에 있는 `int a, int b`가 매개변수이다.

매개변수는 메서드가 외부에서 전달받은 값을 저장하는 변수이다.

```text
매개변수
→ 메서드가 입력받은 값을 저장하는 변수
```

예를 들어 다음처럼 호출하면:

```java
add(1, 2)
```

값이 이렇게 전달된다.

```text
a = 1
b = 2
```

다음처럼 호출하면:

```java
add(10, 20)
```

값이 이렇게 전달된다.

```text
a = 10
b = 20
```

즉, `a`와 `b`는 메서드 안에서 사용할 수 있는 변수이다.

---

## 8. 인수와 매개변수

다음 코드를 보자.

```java
int result = add(1, 2);
```

여기서 `1`, `2`는 메서드를 호출할 때 실제로 넣는 값이다.

이런 값을 인수 또는 인자라고 한다.

```text
인수 또는 인자
→ 메서드를 호출할 때 실제로 넣는 값
→ add(1, 2)의 1과 2
```

반면 메서드를 정의하는 부분의 `a`, `b`는 매개변수이다.

```java
public static int add(int a, int b)
```

```text
매개변수
→ 메서드가 전달받은 값을 저장하는 변수
→ int a, int b
```

정리하면 다음과 같다.

```text
add(1, 2)
→ 1, 2는 인수

public static int add(int a, int b)
→ a, b는 매개변수
```

쉽게 말하면 다음과 같다.

```text
인수
→ 보내는 값

매개변수
→ 받는 변수
```

---

## 9. 메서드 본문

메서드 본문은 중괄호 `{}` 안에 있는 코드이다.

```java
{
    int sum = a + b;
    return sum;
}
```

이 부분이 실제로 메서드가 수행하는 작업이다.

`add` 메서드의 본문은 다음 일을 한다.

```text
1. a와 b를 더한다.
2. 더한 값을 sum에 저장한다.
3. sum을 return으로 돌려준다.
```

즉, 메서드를 호출하면 메서드 본문이 위에서 아래로 실행된다.

---

## 10. 매개변수가 없는 메서드

메서드는 꼭 매개변수를 가져야 하는 것은 아니다.

입력값이 필요 없는 메서드는 매개변수를 작성하지 않아도 된다.

예를 들어 프로그램 시작 문구를 출력하는 메서드는 외부에서 값을 받을 필요가 없다.

```java
public static void printHeader() {
    System.out.println("프로그램을 시작합니다.");
}
```

이 메서드는 괄호 안이 비어 있다.

```java
printHeader()
```

즉, 매개변수가 없는 메서드이다.

호출할 때도 값을 넣지 않는다.

```java
printHeader();
```

정리하면 다음과 같다.

```text
매개변수가 없는 메서드
→ 외부에서 입력값을 받을 필요가 없는 메서드
→ 괄호 안을 비워둔다.
```

---

## 11. 반환 타입이 없는 메서드

메서드가 값을 반환하지 않을 수도 있다.

이때는 반환 타입에 `void`를 사용한다.

```java
public static void printHeader() {
    System.out.println("프로그램을 시작합니다.");
}
```

여기서 `void`는 반환할 값이 없다는 뜻이다.

```text
void
→ 반환값이 없다.
```

이 메서드는 단순히 문장을 출력만 한다.

어떤 값을 계산해서 호출한 곳으로 돌려주지 않는다.

그래서 다음처럼 그냥 호출만 한다.

```java
printHeader();
```

반환값이 없기 때문에 변수에 저장할 수 없다.

```java
int result = printHeader(); // 오류
```

이 코드는 오류이다.

왜냐하면 `printHeader()`는 돌려주는 값이 없기 때문이다.

---

## 12. return이 있는 메서드

값을 반환하는 메서드는 `return`을 사용한다.

```java
public static int add(int a, int b) {
    int sum = a + b;
    return sum;
}
```

이 메서드는 `int` 값을 반환한다.

그래서 호출 결과를 변수에 저장할 수 있다.

```java
int result = add(1, 2);
```

실행 흐름은 다음과 같다.

```text
1. add(1, 2)를 호출한다.
2. a에는 1이 들어간다.
3. b에는 2가 들어간다.
4. sum = a + b를 실행한다.
5. sum은 3이 된다.
6. return sum으로 3을 돌려준다.
7. add(1, 2) 자리가 3으로 바뀐다.
8. result에 3이 저장된다.
```

즉:

```java
int result = add(1, 2);
```

는 결과적으로 다음처럼 이해할 수 있다.

```java
int result = 3;
```

---

## 13. return의 의미

```java
return sum;
```

`return`은 메서드의 결과를 호출한 곳으로 돌려주는 역할을 한다.

예를 들어:

```java
public static int add(int a, int b) {
    int sum = a + b;
    return sum;
}
```

여기서 `a = 1`, `b = 2`라면:

```text
sum = 1 + 2
sum = 3
return sum
return 3
```

따라서 `add(1, 2)`의 결과는 3이 된다.

정리하면 다음과 같다.

```text
return
→ 메서드의 결과를 호출한 곳으로 돌려준다.
```

---

## 14. return은 메서드를 종료한다

`return`은 값을 돌려주는 역할도 하지만,
메서드를 끝내는 역할도 한다.

```java
public static int add(int a, int b) {
    int sum = a + b;
    return sum;
}
```

`return sum;`이 실행되면 메서드는 종료된다.

따라서 `return` 아래에 실행할 수 없는 코드를 작성하면 문제가 생길 수 있다.

```java
public static int add(int a, int b) {
    int sum = a + b;
    return sum;
    // System.out.println("끝"); // return 이후라 실행될 수 없음
}
```

지금 단계에서는 다음처럼 기억하면 된다.

```text
return
→ 값을 돌려준다.
→ 메서드를 끝낸다.
```

---

## 15. void 메서드에서 return

`void` 메서드는 반환값이 없다.

그래서 보통 `return 값;`을 작성하지 않는다.

```java
public static void printHeader() {
    System.out.println("프로그램을 시작합니다.");
}
```

하지만 `void` 메서드에서도 메서드를 중간에 종료하고 싶을 때는 `return;`만 사용할 수 있다.

```java
public static void checkAge(int age) {
    if (age < 0) {
        return;
    }

    System.out.println("나이: " + age);
}
```

여기서 `return;`은 값을 반환하는 것이 아니라,
메서드를 여기서 끝내라는 뜻이다.

정리하면 다음과 같다.

```text
int, double, String 반환 타입
→ return 값; 필요

void 반환 타입
→ 반환값 없음
→ 필요하면 return; 으로 메서드 종료 가능
```

---

## 16. 메서드 호출과 값 전달

메서드를 호출할 때는 변수 자체가 넘어가는 것이 아니라,
변수 안에 들어있는 값이 복사되어 넘어간다.

예를 들어 다음 코드가 있다.

```java
package method;

public class MethodValue3 {
    public static void main(String[] args) {
        int num1 = 5;
        System.out.println("number 변경전 " + num1);

        num1 = changeNumber(num1);

        System.out.println("number 변경후 " + num1);
    }

    public static int changeNumber(int num2) {
        num2 = num2 * 2;
        return num2;
    }
}
```

처음 상태는 다음과 같다.

```text
num1 = 5
```

다음 코드가 실행된다.

```java
num1 = changeNumber(num1);
```

이 줄은 오른쪽부터 실행된다.

```text
changeNumber(num1)
→ changeNumber(5)
```

`num1` 자체가 넘어가는 것이 아니라,
`num1` 안에 있던 값 5가 복사되어 `num2`로 전달된다.

```text
num1 = 5
num2 = 5
```

메서드 안에서는 다음 코드가 실행된다.

```java
num2 = num2 * 2;
```

그러면:

```text
num2 = 5 * 2
num2 = 10
```

그리고 다음 코드가 실행된다.

```java
return num2;
```

이때 `num2` 값 10이 반환된다.

```text
return 10
```

그래서 `changeNumber(num1)` 자리는 10으로 바뀐다.

```java
num1 = changeNumber(num1);
num1 = 10;
```

따라서 최종적으로 `num1`은 10이 된다.

---

## 17. num1이 바뀌는 진짜 이유

중요한 점은 아래 메서드가 직접 위의 `num1`을 바꾸는 것이 아니라는 점이다.

`changeNumber` 메서드는 다음 일만 한다.

```text
1. 5를 받는다.
2. num2에 저장한다.
3. num2를 2배 해서 10을 만든다.
4. 10을 return한다.
```

진짜 `num1`이 10으로 바뀌는 이유는 이 코드 때문이다.

```java
num1 = changeNumber(num1);
```

이 코드는 `changeNumber(num1)`의 반환값을 다시 `num1`에 저장한다.

그래서 다음처럼 되는 것이다.

```java
num1 = changeNumber(num1);
num1 = 10;
```

만약 이렇게만 쓰면:

```java
changeNumber(num1);
```

`changeNumber`가 10을 만들고 return해도,
그 값을 아무 변수에도 저장하지 않는다.

그래서 `num1`은 그대로 5이다.

정리하면 다음과 같다.

```text
num1 = changeNumber(num1);
→ 반환된 10을 num1에 다시 저장한다.
→ num1이 10으로 바뀐다.

changeNumber(num1);
→ 반환된 10을 저장하지 않는다.
→ num1은 그대로 5이다.
```

---

## 18. 메서드 호출식과 반환값

다음 코드는 메서드 호출식이다.

```java
changeNumber(num1)
```

이 자체가 처음부터 10인 것은 아니다.

실행 순서는 다음과 같다.

```text
1. changeNumber(num1)을 호출한다.
2. num1의 값 5가 num2로 복사된다.
3. changeNumber 메서드 본문이 실행된다.
4. num2가 10이 된다.
5. return num2로 10을 반환한다.
6. changeNumber(num1) 자리가 10으로 바뀐다.
```

즉:

```text
changeNumber(num1)
→ 메서드 호출

changeNumber(num1)이 실행된 결과
→ return 값
```

한 줄로 정리하면 다음과 같다.

```text
메서드 호출식은 실행이 끝나면 반환값으로 바뀐다.
```

---

## 19. 메서드와 형변환

메서드를 호출할 때는 전달하는 인수의 타입과 매개변수의 타입이 맞아야 한다.

하지만 타입이 정확히 같지 않아도 자동 형변환이 가능한 경우에는 호출할 수 있다.

예를 들어 다음 메서드가 있다.

```java
public static void printNumber(double n) {
    System.out.println("숫자: " + n);
}
```

이 메서드는 `double` 타입의 값을 받는다.

그런데 다음처럼 `int` 값을 전달할 수 있다.

```java
int number = 100;
printNumber(number);
```

이 경우 `int` 값 100이 `double`로 자동 형변환된다.

개념적으로는 다음과 같다.

```text
printNumber(number)
printNumber(100)
printNumber(100.0)
```

왜냐하면 `double`이 `int`보다 더 넓은 범위의 숫자를 표현할 수 있기 때문이다.

정리하면 다음과 같다.

```text
메서드를 호출할 때 인수 타입과 매개변수 타입이 맞아야 한다.
단, 자동 형변환이 가능한 경우에는 호출할 수 있다.
```

---

## 20. 자동 형변환이 가능한 경우

다음 메서드는 `double` 타입을 받는다.

```java
public static void printNumber(double n) {
    System.out.println("숫자: " + n);
}
```

그런데 `int` 값을 넣어도 된다.

```java
printNumber(100);
```

이유는 `int`가 `double`로 자동 형변환될 수 있기 때문이다.

```text
100
→ 100.0
```

그래서 다음 호출은 가능하다.

```java
printNumber(100);
```

하지만 반대로 `double` 값을 `int` 매개변수에 자동으로 넣는 것은 안 된다.

```java
public static void printInt(int n) {
    System.out.println(n);
}
```

```java
printInt(1.5); // 오류
```

`double`은 소수점을 가질 수 있고 `int`는 정수만 저장하기 때문에,
값 손실이 발생할 수 있다.

이런 경우 자동 형변환이 되지 않는다.

---

## 21. 메서드 오버로딩

메서드 오버로딩은 같은 이름의 메서드를 여러 개 정의하는 것이다.

단, 이름만 같고 매개변수가 달라야 한다.

```text
메서드 오버로딩
→ 같은 이름의 메서드를 여러 개 정의하는 것
→ 단, 매개변수 정보가 달라야 한다
```

예를 들어 다음과 같은 메서드들을 만들 수 있다.

```java
add(int a, int b)
add(int a, int b, int c)
add(double a, double b)
```

이 메서드들은 이름은 모두 `add`이다.

하지만 매개변수가 다르다.

```text
add(int a, int b)
→ int 2개

add(int a, int b, int c)
→ int 3개

add(double a, double b)
→ double 2개
```

그래서 자바는 이 메서드들을 서로 다른 메서드로 구분할 수 있다.

---

## 22. 오버로딩이 필요한 이유

두 수를 더하는 메서드와 세 수를 더하는 메서드를 만들고 싶다고 하자.

기능은 모두 더하기이다.

그러면 이름을 각각 다르게 만들 수도 있다.

```java
addTwoNumbers()
addThreeNumbers()
```

하지만 둘 다 더하기 기능이므로 같은 이름인 `add`를 사용하는 것이 더 자연스럽다.

자바는 메서드 이름뿐만 아니라 매개변수 정보까지 보고 메서드를 구분한다.

그래서 다음처럼 같은 이름의 메서드를 여러 개 만들 수 있다.

```java
public static int add(int a, int b) {
    return a + b;
}

public static int add(int a, int b, int c) {
    return a + b + c;
}
```

호출할 때 인수가 2개이면 첫 번째 메서드가 실행된다.

```java
add(1, 2)
```

호출할 때 인수가 3개이면 두 번째 메서드가 실행된다.

```java
add(1, 2, 3)
```

---

## 23. 매개변수 개수가 다른 오버로딩

다음 코드를 보자.

```java
package overloading;

public class Overloading1 {
    public static void main(String[] args) {
        System.out.println("1: " + add(1, 2));
        System.out.println("2: " + add(1, 2, 3));
    }

    public static int add(int a, int b) {
        System.out.println("1번 호출");
        return a + b;
    }

    public static int add(int a, int b, int c) {
        System.out.println("2번 호출");
        return a + b + c;
    }
}
```

두 메서드의 이름은 같다.

```java
add
add
```

하지만 매개변수 개수가 다르다.

```java
add(int a, int b)
```

```java
add(int a, int b, int c)
```

첫 번째 메서드는 정수 2개를 받는다.

두 번째 메서드는 정수 3개를 받는다.

그래서 오버로딩이 가능하다.

호출할 때:

```java
add(1, 2)
```

는 인수가 2개이므로 첫 번째 메서드가 호출된다.

호출할 때:

```java
add(1, 2, 3)
```

는 인수가 3개이므로 두 번째 메서드가 호출된다.

---

## 24. 매개변수 타입이 다른 오버로딩

매개변수 개수가 같아도 타입이 다르면 오버로딩이 가능하다.

```java
public static int add(int a, int b) {
    System.out.println("1번 호출");
    return a + b;
}

public static double add(double a, double b) {
    System.out.println("2번 호출");
    return a + b;
}
```

호출할 때:

```java
add(1, 2)
```

는 `int`, `int` 값을 전달한다.

그래서 다음 메서드가 호출된다.

```java
add(int a, int b)
```

호출할 때:

```java
add(1.2, 1.5)
```

는 `double`, `double` 값을 전달한다.

그래서 다음 메서드가 호출된다.

```java
add(double a, double b)
```

정리하면 다음과 같다.

```text
매개변수 타입이 다르면 오버로딩 가능
```

---

## 25. 매개변수 순서가 다른 오버로딩

매개변수의 개수와 타입 종류가 같아도 순서가 다르면 오버로딩이 가능하다.

예를 들어 다음 코드가 있다.

```java
package overloading;

public class Overloading2 {
    public static void main(String[] args) {
        myMethod(1, 1.2);
        myMethod(1.2, 2);
    }

    public static void myMethod(int a, double b) {
        System.out.println("int a, double b");
    }

    public static void myMethod(double a, int b) {
        System.out.println("double a, int b");
    }
}
```

두 메서드의 이름은 같다.

```java
myMethod
myMethod
```

하지만 매개변수 순서가 다르다.

```java
myMethod(int a, double b)
```

```java
myMethod(double a, int b)
```

첫 번째는 `int`, `double` 순서이다.

두 번째는 `double`, `int` 순서이다.

그래서 자바는 두 메서드를 서로 다른 메서드로 구분할 수 있다.

---

## 26. myMethod 호출 흐름

```java
myMethod(1, 1.2);
```

여기서 인수의 타입은 다음과 같다.

```text
1
→ int

1.2
→ double
```

즉 호출 형태는 다음과 같다.

```java
myMethod(int, double)
```

그래서 이 메서드가 호출된다.

```java
public static void myMethod(int a, double b) {
    System.out.println("int a, double b");
}
```

출력 결과는 다음과 같다.

```text
int a, double b
```

다음 호출도 보자.

```java
myMethod(1.2, 2);
```

여기서 인수의 타입은 다음과 같다.

```text
1.2
→ double

2
→ int
```

즉 호출 형태는 다음과 같다.

```java
myMethod(double, int)
```

그래서 이 메서드가 호출된다.

```java
public static void myMethod(double a, int b) {
    System.out.println("double a, int b");
}
```

출력 결과는 다음과 같다.

```text
double a, int b
```

---

## 27. 왜 main에서 myMethod를 호출해야 할까?

아래에 메서드를 정의해두기만 하면 자동으로 실행되는 것이 아니다.

```java
public static void myMethod(int a, double b) {
    System.out.println("int a, double b");
}

public static void myMethod(double a, int b) {
    System.out.println("double a, int b");
}
```

이 코드는 기능을 만들어둔 것이다.

하지만 실행하려면 `main()`에서 호출해야 한다.

```java
myMethod(1, 1.2);
myMethod(1.2, 2);
```

즉:

```text
메서드 정의
→ 기능을 만들어둔 것

메서드 호출
→ 만들어둔 기능을 실행하는 것
```

만약 `main()` 안에서 호출하지 않으면 출력은 아무것도 나오지 않는다.

```java
public static void main(String[] args) {
}
```

이렇게 비어 있으면 아래 메서드들이 있어도 실행되지 않는다.

정리하면 다음과 같다.

```text
메서드는 만들어두기만 하면 실행되지 않는다.
반드시 호출해야 실행된다.
```

---

## 28. 오버로딩 실패 예시

반환 타입만 다른 것은 오버로딩으로 인정되지 않는다.

예를 들어 다음 코드는 오버로딩에 실패한다.

```java
int add(int a, int b)
double add(int a, int b)
```

겉으로 보면 반환 타입이 다르다.

```text
첫 번째 메서드 반환 타입 → int
두 번째 메서드 반환 타입 → double
```

하지만 매개변수는 같다.

```text
add(int a, int b)
add(int a, int b)
```

자바는 메서드를 구분할 때 반환 타입만으로 구분하지 않는다.

그래서 이 두 메서드는 같은 메서드로 판단되어 컴파일 오류가 발생한다.

정리하면 다음과 같다.

```text
반환 타입만 다르면 오버로딩 실패
```

---

## 29. 메서드 시그니처

메서드 시그니처는 자바가 메서드를 구분하는 기준이다.

```text
메서드 시그니처
= 메서드 이름 + 매개변수 타입과 순서
```

예를 들어 다음 메서드가 있다.

```java
add(int a, int b)
```

이 메서드의 시그니처는 다음과 같이 볼 수 있다.

```text
add(int, int)
```

다음 메서드는 시그니처가 다르다.

```java
add(int a, int b, int c)
```

```text
add(int, int, int)
```

다음 메서드도 시그니처가 다르다.

```java
add(double a, double b)
```

```text
add(double, double)
```

그래서 이들은 오버로딩이 가능하다.

하지만 다음 두 메서드는 시그니처가 같다.

```java
int add(int a, int b)
double add(int a, int b)
```

두 메서드 모두 시그니처는 다음과 같다.

```text
add(int, int)
```

반환 타입은 시그니처에 포함되지 않는다.

따라서 이 경우에는 오버로딩이 불가능하다.

---

## 30. 오버로딩 규칙 정리

오버로딩이 가능한 경우는 다음과 같다.

```text
1. 메서드 이름이 같다.
2. 매개변수 개수가 다르다.
3. 또는 매개변수 타입이 다르다.
4. 또는 매개변수 타입의 순서가 다르다.
```

예시:

```java
add(int a, int b)
add(int a, int b, int c)
add(double a, double b)
myMethod(int a, double b)
myMethod(double a, int b)
```

오버로딩이 불가능한 경우는 다음과 같다.

```text
1. 메서드 이름이 같다.
2. 매개변수 개수, 타입, 순서가 모두 같다.
3. 반환 타입만 다르다.
```

예시:

```java
int add(int a, int b)
double add(int a, int b)
```

이 경우 반환 타입은 다르지만 매개변수 정보가 같기 때문에 오버로딩이 아니다.

---

## 31. 오늘 헷갈렸던 부분 정리

오늘 헷갈렸던 부분은 다음이었다.

```text
1. 메서드 정의가 정확히 어떤 구조인지
2. return이 왜 필요한지
3. changeNumber(num1)이 왜 10으로 바뀌는지
4. 아래 메서드가 직접 num1을 바꾸는 것인지
5. 오버로딩에서 main에 myMethod를 왜 써야 하는지
6. 같은 이름의 메서드를 자바가 어떻게 구분하는지
```

정리하면 다음과 같다.

```text
메서드 정의
→ 제어자, 반환 타입, 메서드 이름, 매개변수, 본문으로 이루어진다.

return
→ 메서드 결과를 호출한 곳으로 돌려준다.
→ 메서드 호출식은 실행이 끝나면 반환값으로 바뀐다.

changeNumber(num1)
→ num1의 값 5가 num2로 복사된다.
→ num2가 10이 된다.
→ 10을 return한다.
→ changeNumber(num1) 자리가 10으로 바뀐다.

num1 = changeNumber(num1)
→ 반환된 10을 다시 num1에 저장한다.
→ 그래서 num1이 10으로 바뀐다.

myMethod(1, 1.2)
→ 아래에 정의된 myMethod 중에서 int, double을 받는 메서드를 실행하라는 뜻이다.

메서드는 정의만 하면 실행되지 않는다.
반드시 호출해야 실행된다.

오버로딩
→ 같은 이름의 메서드를 여러 개 정의하는 것
→ 단, 매개변수 정보가 달라야 한다.
```

---

## 32. 내가 이해한 핵심

이번 범위에서 가장 중요한 것은 메서드가 기능을 나누는 도구라는 점이다.

메서드는 다음 구조로 정의한다.

```java
제어자 반환타입 메서드이름(매개변수 목록) {
    메서드 본문
}
```

메서드를 호출하면 메서드 본문이 실행된다.

반환값이 있는 메서드는 `return`으로 결과를 돌려준다.

```java
int result = add(1, 2);
```

이 코드는 `add(1, 2)`가 실행된 후 반환값으로 바뀌고,
그 값이 `result`에 저장된다.

오버로딩은 같은 이름의 메서드를 여러 개 만드는 것이다.

하지만 아무렇게나 같은 이름을 쓸 수 있는 것이 아니라,
매개변수의 개수, 타입, 순서가 달라야 한다.

반환 타입만 다른 것은 오버로딩이 아니다.

---

## 33. 내가 만들려는 프로젝트와의 연결

내가 만들고 싶은 프로젝트는 패션 추천 시스템이다.

이 시스템은 사용자가 입력한 옷 정보를 바탕으로 색상, 핏, 기장, 상황, 분위기 등을 분석해서 옷 조합을 추천하는 방향이다.

메서드는 이 프로젝트에서 기능을 나누는 데 중요하다.

예를 들어 모든 코드를 `main()`에 넣으면 코드가 너무 길어진다.

그래서 기능별로 메서드를 나눌 수 있다.

```text
색상 점수 계산
핏 점수 계산
상황 적합도 점수 계산
평균 점수 계산
추천 결과 출력
```

예를 들어 색상 점수를 계산하는 메서드는 다음처럼 만들 수 있다.

```java
public static int getColorScore(String color) {
    if (color.equals("black")) {
        return 90;
    } else if (color.equals("navy")) {
        return 80;
    } else {
        return 60;
    }
}
```

평균 점수를 계산하는 메서드는 다음처럼 만들 수 있다.

```java
public static double getAverageScore(int colorScore, int fitScore, int moodScore) {
    int total = colorScore + fitScore + moodScore;
    return (double) total / 3;
}
```

오버로딩도 나중에 사용할 수 있다.

예를 들어 점수 계산 기준이 2개일 때와 3개일 때 같은 이름의 메서드를 사용할 수 있다.

```java
public static double getAverageScore(int colorScore, int fitScore) {
    return (double) (colorScore + fitScore) / 2;
}

public static double getAverageScore(int colorScore, int fitScore, int moodScore) {
    return (double) (colorScore + fitScore + moodScore) / 3;
}
```

두 메서드는 이름은 같지만 매개변수 개수가 다르다.

그래서 오버로딩이 가능하다.

이렇게 하면 나중에 추천 시스템에서 계산 기준이 달라져도 같은 이름의 메서드로 자연스럽게 처리할 수 있다.

---

## 34. 복학 전 공부 흐름에서의 의미

지금은 Java 기본기를 다시 잡는 과정이다.

배열까지는 여러 값을 저장하고 반복문으로 처리하는 방법을 배웠다.

메서드부터는 코드를 기능 단위로 나누는 연습이 시작된다.

이번 범위에서 중요한 것은 다음이다.

```text
메서드는 기능을 나누는 도구이다.
메서드는 정의와 호출이 다르다.
정의만 하면 실행되지 않는다.
호출해야 실행된다.
return은 결과를 호출한 곳으로 돌려준다.
메서드 호출식은 실행 후 반환값으로 바뀐다.
메서드 호출 시 변수 자체가 아니라 값이 복사되어 전달된다.
오버로딩은 같은 이름의 메서드를 여러 개 정의하는 것이다.
오버로딩은 매개변수 개수, 타입, 순서가 달라야 가능하다.
반환 타입만 다른 것은 오버로딩이 아니다.
```

이 내용을 이해하면 앞으로 문제를 풀 때도 코드를 더 깔끔하게 나눌 수 있을 것 같다.

---

## 35. 다음 공부 계획

다음에는 메서드 단원의 문제와 풀이를 풀면서,
메서드를 직접 정의하고 호출하는 연습을 해야겠다.

특히 다음 내용을 더 연습해야겠다.

```text
1. 문제에서 반복되는 기능 찾기
2. 메서드 이름 정하기
3. 매개변수가 필요한지 판단하기
4. 반환값이 필요한지 판단하기
5. 반환 타입 정하기
6. return 작성하기
7. 메서드 호출 결과를 변수에 저장하기
8. 오버로딩 조건 구분하기
```

코드를 바로 외우기보다,
이 기능이 입력값이 필요한지,
결과값을 돌려줘야 하는지부터 생각해야겠다.
