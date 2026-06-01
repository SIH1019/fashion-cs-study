# 2026-06-01 Java 연산자 학습 개발일지

## 1. 오늘 공부한 주제

- Java 연산자
- 산술 연산자
- 문자열 더하기
- 증감 연산자
- 비교 연산자
- 논리 연산자
- 대입 연산자
- 연산자 우선순위

---

## 2. 오늘 공부한 범위

- 연산자 시작
- 산술 연산자
- 문자열 더하기
- 증감 연산자
- 비교 연산자
- 논리 연산자
- 대입 연산자
- 연산자 우선순위

---

## 3. 오늘 공부하지 않은 범위

- 조건문
- 반복문
- 메서드
- 배열
- 객체지향
- 자료구조

---

## 4. 연산자란?

- 연산자는 계산이나 비교, 대입 같은 작업을 할 때 사용하는 기호이다.
- Java에서는 숫자 계산뿐만 아니라 문자열 연결, 값 비교, 논리 판단, 값 저장에도 연산자를 사용한다.
- 연산자는 변수에 저장된 값을 가지고 새로운 결과를 만들 수 있다.

예시:

```java
int a = 10;
int b = 3;

System.out.println(a + b);
System.out.println(a > b);
```

- `+`
  - 덧셈 연산자

- `>`
  - 비교 연산자

---

## 5. 산술 연산자

- 산술 연산자는 숫자 계산에 사용하는 연산자이다.
- 덧셈, 뺄셈, 곱셈, 나눗셈, 나머지 계산을 할 수 있다.

정리:

```text
+  → 더하기
-  → 빼기
*  → 곱하기
/  → 나누기
%  → 나머지
```

예시:

```java
int a = 10;
int b = 3;

System.out.println(a + b);
System.out.println(a - b);
System.out.println(a * b);
System.out.println(a / b);
System.out.println(a % b);
```

실행 결과:

```text
13
7
30
3
1
```

---

## 6. 나눗셈 연산

```java
int a = 10;
int b = 3;

System.out.println(a / b);
```

- `10 / 3`의 결과는 `3`이다.
- `int`끼리 나누면 결과도 정수로 나온다.
- 소수점 아래 값은 버려진다.

정리:

```text
10 / 3 = 3
```

- 수학적으로는 `3.333...`이지만, Java에서 `int`끼리 나누면 정수 결과만 남는다.

---

## 7. 나머지 연산자

```java
int a = 10;
int b = 3;

System.out.println(a % b);
```

- `%`는 나머지를 구하는 연산자이다.
- `10 % 3`은 `10`을 `3`으로 나누고 남은 나머지를 구한다.
- 결과는 `1`이다.

정리:

```text
10 / 3 = 몫 3, 나머지 1
10 % 3 = 1
```

- 나머지 연산자는 짝수/홀수 판단, 배수 판단에서 자주 사용된다.

예시:

```java
int number = 10;

System.out.println(number % 2);
```

- 결과가 `0`이면 짝수이다.
- 결과가 `1`이면 홀수이다.

---

## 8. 문자열 더하기

- `+` 연산자는 숫자끼리 사용하면 덧셈을 한다.
- 문자열과 함께 사용하면 문자열을 연결한다.

예시:

```java
String result = "hello" + " java";
System.out.println(result);
```

실행 결과:

```text
hello java
```

---

## 9. 문자열과 숫자 더하기

```java
String result = "a + b = " + 10;
System.out.println(result);
```

실행 결과:

```text
a + b = 10
```

- 문자열과 숫자를 `+`로 연결하면 숫자가 문자열처럼 붙는다.
- 문자열이 하나라도 포함되면 `+`는 문자열 연결 역할을 한다.

예시:

```java
System.out.println("result = " + 10 + 20);
```

실행 결과:

```text
result = 1020
```

- `"result = " + 10`이 먼저 문자열이 된다.
- 그 뒤에 `20`도 문자열처럼 이어 붙는다.

주의:

```java
System.out.println(10 + 20 + " result");
```

실행 결과:

```text
30 result
```

- 앞의 `10 + 20`이 먼저 계산된다.
- 그 결과 `30`이 문자열과 연결된다.

---

## 10. 증감 연산자

- 증감 연산자는 변수 값을 1 증가시키거나 1 감소시킬 때 사용한다.

정리:

```text
++  → 1 증가
--  → 1 감소
```

예시:

```java
int a = 0;

a++;
System.out.println(a);

a--;
System.out.println(a);
```

실행 결과:

```text
1
0
```

---

## 11. 전위 증감과 후위 증감

### 11-1. 전위 증감

```java
int a = 1;
int b = ++a;

System.out.println(a);
System.out.println(b);
```

실행 결과:

```text
2
2
```

- `++a`는 먼저 `a`를 1 증가시킨다.
- 그 다음 증가된 값을 사용한다.
- 그래서 `a`도 `2`, `b`도 `2`가 된다.

---

### 11-2. 후위 증감

```java
int a = 1;
int b = a++;

System.out.println(a);
System.out.println(b);
```

실행 결과:

```text
2
1
```

- `a++`는 먼저 현재 `a` 값을 사용한다.
- 그 다음 `a`를 1 증가시킨다.
- 그래서 `b`에는 기존 값 `1`이 들어가고, `a`는 나중에 `2`가 된다.

---

## 12. 비교 연산자

- 비교 연산자는 두 값을 비교할 때 사용한다.
- 비교 결과는 `true` 또는 `false`로 나온다.

정리:

```text
==  → 같다
!=  → 같지 않다
>   → 크다
<   → 작다
>=  → 크거나 같다
<=  → 작거나 같다
```

예시:

```java
int a = 10;
int b = 20;

System.out.println(a == b);
System.out.println(a != b);
System.out.println(a < b);
System.out.println(a > b);
```

실행 결과:

```text
false
true
true
false
```

---

## 13. 비교 연산자 주의점

```java
int a = 10;
int b = 10;

System.out.println(a == b);
```

- `==`는 두 값이 같은지 비교한다.
- `=`는 오른쪽 값을 왼쪽 변수에 저장한다.

정리:

```text
=   → 대입
==  → 비교
```

- `=`와 `==`는 의미가 완전히 다르다.
- 조건을 비교할 때는 `==`를 사용해야 한다.

---

## 14. 논리 연산자

- 논리 연산자는 여러 조건을 함께 판단할 때 사용한다.
- 결과는 `true` 또는 `false`로 나온다.

정리:

```text
&&  → 그리고
||  → 또는
!   → 부정
```

---

## 15. && 연산자

```java
int age = 22;
boolean isStudent = true;

System.out.println(age >= 20 && isStudent);
```

- `&&`는 양쪽 조건이 모두 참일 때만 `true`가 된다.

정리:

```text
true && true   → true
true && false  → false
false && true  → false
false && false → false
```

---

## 16. || 연산자

```java
int age = 17;
boolean hasPermission = true;

System.out.println(age >= 20 || hasPermission);
```

- `||`는 둘 중 하나만 참이어도 `true`가 된다.

정리:

```text
true || true   → true
true || false  → true
false || true  → true
false || false → false
```

---

## 17. ! 연산자

```java
boolean isMatched = true;

System.out.println(!isMatched);
```

실행 결과:

```text
false
```

- `!`는 값을 반대로 바꾼다.
- `true`는 `false`가 된다.
- `false`는 `true`가 된다.

정리:

```text
!true  → false
!false → true
```

---

## 18. 대입 연산자

- 대입 연산자는 오른쪽 값을 왼쪽 변수에 저장할 때 사용한다.

예시:

```java
int a = 10;
```

- `10`을 변수 `a`에 저장한다.
- 여기서 `=`는 같다는 뜻이 아니라 저장한다는 뜻이다.

---

## 19. 복합 대입 연산자

- 복합 대입 연산자는 연산과 대입을 한 번에 처리하는 방식이다.

정리:

```text
a += 3  → a = a + 3
a -= 3  → a = a - 3
a *= 3  → a = a * 3
a /= 3  → a = a / 3
a %= 3  → a = a % 3
```

예시:

```java
int a = 10;

a += 3;
System.out.println(a);
```

실행 결과:

```text
13
```

- `a += 3`은 `a = a + 3`과 같은 의미이다.
- 기존 `a` 값에 `3`을 더한 뒤 다시 `a`에 저장한다.

---

## 20. 연산자 우선순위

- 연산자 우선순위는 여러 연산자가 함께 있을 때 어떤 연산을 먼저 할지 정하는 규칙이다.
- 수학에서 곱셈을 덧셈보다 먼저 계산하는 것과 비슷하다.

예시:

```java
int result = 2 + 3 * 4;
System.out.println(result);
```

실행 결과:

```text
14
```

- `3 * 4`가 먼저 계산된다.
- 그 다음 `2 + 12`가 계산된다.
- 최종 결과는 `14`이다.

---

## 21. 괄호를 사용한 우선순위 변경

```java
int result = (2 + 3) * 4;
System.out.println(result);
```

실행 결과:

```text
20
```

- 괄호 안의 `2 + 3`이 먼저 계산된다.
- 그 다음 `5 * 4`가 계산된다.
- 최종 결과는 `20`이다.

---

## 22. 자주 보는 연산자 우선순위

- 괄호가 가장 먼저 계산된다.
- 증감 연산자가 산술 연산자보다 우선한다.
- 곱셈, 나눗셈, 나머지가 덧셈, 뺄셈보다 먼저 계산된다.
- 비교 연산자는 산술 연산자보다 나중에 계산된다.
- 논리 연산자는 비교 연산자보다 나중에 계산된다.
- 대입 연산자는 가장 나중에 계산된다.

정리:

```text
1. 괄호 ()
2. 증감 연산자 ++, --
3. 곱셈 / 나눗셈 / 나머지 *, /, %
4. 덧셈 / 뺄셈 +, -
5. 비교 연산자 <, <=, >, >=, ==, !=
6. 논리 연산자 &&, ||
7. 대입 연산자 =
```

---

## 23. 우선순위보다 괄호를 우선 사용하기

- 연산자 우선순위를 모두 외우려고 하지 않아도 된다.
- 헷갈리는 식은 괄호를 사용하면 된다.
- 괄호를 사용하면 계산 순서가 명확해진다.
- 코드를 읽는 사람도 이해하기 쉬워진다.

예시:

```java
int result = (2 + 3) * 4;
```

- 괄호를 사용해서 먼저 계산할 부분을 명확히 표시했다.

---

## 24. 오늘 작성한 예제 코드

```java
package operator;

public class OperatorPractice {
    public static void main(String[] args) {
        int a = 10;
        int b = 3;

        System.out.println(a + b);
        System.out.println(a - b);
        System.out.println(a * b);
        System.out.println(a / b);
        System.out.println(a % b);

        String topColor = "navy";
        String bottomColor = "black";
        System.out.println("상의 색상: " + topColor);
        System.out.println("하의 색상: " + bottomColor);

        int colorScore = 82;
        int fitScore = 78;
        int totalScore = colorScore + fitScore;

        System.out.println("전체 점수: " + totalScore);

        boolean isHighScore = totalScore >= 150;
        boolean isColorMatched = true;

        System.out.println(isHighScore && isColorMatched);
    }
}
```

실행 결과:

```text
13
7
30
3
1
상의 색상: navy
하의 색상: black
전체 점수: 160
true
```

---

## 25. 오늘 새로 알게 된 점

- 연산자는 계산, 비교, 대입, 논리 판단에 사용된다.
- `+`는 숫자끼리 사용하면 덧셈이고, 문자열과 함께 사용하면 문자열 연결이다.
- `int`끼리 나누면 결과도 정수로 나온다.
- `%`는 나머지를 구하는 연산자이다.
- `++`와 `--`는 값을 1씩 증가하거나 감소시킨다.
- 전위 증감은 먼저 증가시키고 값을 사용한다.
- 후위 증감은 먼저 값을 사용하고 나중에 증가시킨다.
- 비교 연산자의 결과는 `true` 또는 `false`이다.
- `=`는 대입이고, `==`는 비교이다.
- 논리 연산자는 여러 조건을 함께 판단할 때 사용한다.
- 복합 대입 연산자는 연산과 대입을 한 번에 처리한다.
- 연산자에는 계산 순서가 있다.
- 헷갈리는 식은 괄호를 사용하면 된다.

---

## 26. 헷갈린 부분

- `=`와 `==`의 차이가 헷갈릴 수 있다.
- 문자열과 숫자를 `+`로 연결할 때 계산이 아니라 문자열 연결이 되는 경우가 헷갈렸다.
- `int / int` 결과가 소수점 없이 정수로 나오는 점이 헷갈릴 수 있다.
- 전위 증감과 후위 증감의 실행 순서가 헷갈릴 수 있다.
- `&&`와 `||`의 차이가 헷갈릴 수 있다.
- 연산자 우선순위를 모두 외우기보다는 괄호로 명확하게 쓰는 것이 좋다고 느꼈다.

---

## 27. 내 프로젝트와 연결한 부분

- 패션 추천 시스템에서 점수를 계산할 때 산술 연산자를 사용할 수 있다.
- 색상 점수, 핏 점수, 기장 점수를 더해서 전체 점수를 계산할 수 있다.
- 특정 점수 이상인지 판단할 때 비교 연산자를 사용할 수 있다.
- 색상 조합이 맞고 점수도 높은지 확인할 때 논리 연산자를 사용할 수 있다.
- 조건이 복잡해지면 괄호를 사용해서 판단 순서를 명확히 해야 한다.

예시:

```java
int colorScore = 82;
int fitScore = 78;
int lengthScore = 75;

int totalScore = colorScore + fitScore + lengthScore;

boolean isHighScore = totalScore >= 200;
boolean isColorMatched = true;
boolean isRecommended = isHighScore && isColorMatched;

System.out.println(isRecommended);
```

정리:

```text
colorScore   → 색상 점수
fitScore     → 핏 점수
lengthScore  → 기장 점수
totalScore   → 전체 점수
isHighScore  → 전체 점수가 기준 이상인지 판단
isColorMatched → 색상 조합이 적절한지 판단
isRecommended → 추천 가능한 코디인지 판단
```

---

## 28. 오늘의 핵심 정리

- 연산자는 값을 계산하거나 비교하거나 저장할 때 사용한다.
- 산술 연산자는 숫자 계산에 사용한다.
- 문자열과 `+`를 사용하면 문자열 연결이 된다.
- 증감 연산자는 값을 1 증가하거나 감소시킨다.
- 비교 연산자의 결과는 `true` 또는 `false`이다.
- 논리 연산자는 여러 조건을 함께 판단할 때 사용한다.
- 대입 연산자는 오른쪽 값을 왼쪽 변수에 저장한다.
- 복합 대입 연산자는 연산과 대입을 한 번에 처리한다.
- 연산자 우선순위는 계산 순서를 정한다.
- 헷갈리는 연산식은 괄호를 사용하면 된다.
- 패션 추천 시스템에서는 점수 계산, 조건 판단, 추천 여부 판단에 연산자를 사용할 수 있다.

---

## 29. 다음에 할 일

- 연산자 예제 다시 풀기
- 연산자 문제 풀이 정리하기
- 조건문 `if` 공부 시작하기
- 비교 연산자와 논리 연산자를 조건문에 연결해서 이해하기
- 패션 추천 시스템에서 점수 기준으로 추천 여부를 판단하는 코드 작성하기