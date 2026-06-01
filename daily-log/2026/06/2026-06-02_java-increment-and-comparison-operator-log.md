# 2026-06-02 Java 증감 연산자 및 비교 연산자 학습 개발일지

## 1. 오늘 공부한 주제

- 증감 연산자
- 전위 증감 연산자
- 후위 증감 연산자
- 비교 연산자
- `=`와 `==`의 차이
- 비교 연산 결과가 `boolean`으로 나오는 구조

---

## 2. 오늘 공부한 범위

- 증감 연산자
- 전위 증감
- 후위 증감
- 비교 연산자
- 비교 연산자의 결과
- `==`, `!=`, `>`, `<`, `>=`, `<=`

---

## 3. 오늘 공부하지 않은 범위

- 논리 연산자
- 대입 연산자
- 조건문
- 반복문
- 메서드
- 객체지향

---

## 4. 증감 연산자

- 증감 연산자는 변수 값을 1 증가시키거나 1 감소시킬 때 사용한다.
- 값을 1 증가시킬 때는 `++`를 사용한다.
- 값을 1 감소시킬 때는 `--`를 사용한다.
- 변수 값이 일정하게 하나씩 변할 때 자주 사용한다.

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

## 5. 증감 연산자 기본 흐름

```java
int a = 1;

a++;
System.out.println(a);
```

실행 결과:

```text
2
```

- 처음에 `a`에는 `1`이 저장되어 있다.
- `a++`가 실행되면 `a`의 값이 1 증가한다.
- 그래서 `a`의 값은 `2`가 된다.

정리:

```text
a++ → a = a + 1
```

---

## 6. 감소 연산자 기본 흐름

```java
int a = 1;

a--;
System.out.println(a);
```

실행 결과:

```text
0
```

- 처음에 `a`에는 `1`이 저장되어 있다.
- `a--`가 실행되면 `a`의 값이 1 감소한다.
- 그래서 `a`의 값은 `0`이 된다.

정리:

```text
a-- → a = a - 1
```

---

## 7. 전위 증감 연산자

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

- `++a`는 전위 증감 연산자이다.
- 전위 증감은 값을 먼저 증가시킨다.
- 그 다음 증가된 값을 사용한다.
- 그래서 `a`는 먼저 `2`가 된다.
- 그 증가된 값 `2`가 `b`에 저장된다.

실행 흐름:

```text
1. int a = 1;   → a에 1 저장
2. ++a          → a를 먼저 2로 증가
3. int b = ++a; → 증가된 값 2를 b에 저장
4. a 출력       → 2
5. b 출력       → 2
```

정리:

```text
++a → 먼저 증가, 나중에 사용
```

---

## 8. 후위 증감 연산자

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

- `a++`는 후위 증감 연산자이다.
- 후위 증감은 현재 값을 먼저 사용한다.
- 그 다음 변수 값을 증가시킨다.
- 그래서 `b`에는 기존 값 `1`이 먼저 저장된다.
- 그 후 `a`의 값이 `2`가 된다.

실행 흐름:

```text
1. int a = 1;   → a에 1 저장
2. int b = a++; → 현재 a 값 1을 b에 먼저 저장
3. a++          → 이후 a를 2로 증가
4. a 출력       → 2
5. b 출력       → 1
```

정리:

```text
a++ → 먼저 사용, 나중에 증가
```

---

## 9. 전위 증감과 후위 증감 비교

```text
++a → 먼저 증가하고 사용
a++ → 먼저 사용하고 증가
```

비교:

```java
int a = 1;
int b = ++a;
```

- `a` 결과: `2`
- `b` 결과: `2`

```java
int x = 1;
int y = x++;
```

- `x` 결과: `2`
- `y` 결과: `1`

핵심:

```text
혼자 한 줄로 쓸 때는 결과가 비슷해 보인다.
다른 변수에 값을 대입할 때는 전위와 후위의 차이가 나타난다.
```

---

## 10. 비교 연산자

- 비교 연산자는 두 값을 비교할 때 사용한다.
- 비교 연산의 결과는 항상 `true` 또는 `false`이다.
- 비교 결과는 `boolean` 타입으로 저장할 수 있다.

정리:

```text
==  → 같다
!=  → 같지 않다
>   → 크다
<   → 작다
>=  → 크거나 같다
<=  → 작거나 같다
```

---

## 11. 비교 연산자 예시

```java
int a = 10;
int b = 20;

System.out.println(a == b);
System.out.println(a != b);
System.out.println(a > b);
System.out.println(a < b);
System.out.println(a >= b);
System.out.println(a <= b);
```

실행 결과:

```text
false
true
false
true
false
true
```

풀이:

```text
a == b  → 10과 20은 같지 않음 → false
a != b  → 10과 20은 다름 → true
a > b   → 10은 20보다 크지 않음 → false
a < b   → 10은 20보다 작음 → true
a >= b  → 10은 20보다 크거나 같지 않음 → false
a <= b  → 10은 20보다 작거나 같음 → true
```

---

## 12. 비교 연산 결과 저장

```java
int a = 10;
int b = 20;

boolean result = a < b;

System.out.println(result);
```

실행 결과:

```text
true
```

- `a < b`는 `10 < 20`이다.
- 비교 결과는 `true`이다.
- 이 결과를 `boolean result`에 저장할 수 있다.

정리:

```text
비교 연산 결과 → true 또는 false
저장 타입 → boolean
```

---

## 13. `=`와 `==`의 차이

```java
int a = 10;
```

- `=`는 대입 연산자이다.
- 오른쪽 값을 왼쪽 변수에 저장한다.
- `a = 10`은 `a`에 `10`을 저장한다는 뜻이다.

```java
System.out.println(a == 10);
```

- `==`는 비교 연산자이다.
- 두 값이 같은지 비교한다.
- `a == 10`은 `a`의 값이 `10`과 같은지 확인한다.

정리:

```text
=   → 대입, 오른쪽 값을 왼쪽 변수에 저장
==  → 비교, 두 값이 같은지 확인
```

---

## 14. 비교 연산자를 사용할 때 주의할 점

- 값을 저장할 때는 `=`를 사용한다.
- 같은지 비교할 때는 `==`를 사용한다.
- 두 기호를 헷갈리면 코드의 의미가 완전히 달라진다.
- 비교 연산자의 결과는 숫자가 아니라 `true` 또는 `false`이다.
- 비교 결과는 조건문에서 자주 사용된다.

예시:

```java
int score = 85;

boolean isPass = score >= 60;

System.out.println(isPass);
```

실행 결과:

```text
true
```

- `score >= 60`은 `85 >= 60`이므로 `true`이다.
- 이 결과가 `isPass`에 저장된다.

---

## 15. 오늘 작성한 예제 코드

```java
package operator;

public class IncrementComparisonPractice {
    public static void main(String[] args) {
        int a = 1;

        a++;
        System.out.println(a);

        a--;
        System.out.println(a);

        int b = 1;
        int c = ++b;

        System.out.println(b);
        System.out.println(c);

        int x = 1;
        int y = x++;

        System.out.println(x);
        System.out.println(y);

        int score = 85;
        boolean isPass = score >= 60;

        System.out.println(isPass);

        int colorScore = 82;
        int fitScore = 78;

        System.out.println(colorScore == fitScore);
        System.out.println(colorScore != fitScore);
        System.out.println(colorScore > fitScore);
        System.out.println(colorScore < fitScore);
    }
}
```

실행 결과:

```text
2
1
2
2
2
1
true
false
true
true
false
```

---

## 16. 오늘 새로 알게 된 점

- `++`는 변수 값을 1 증가시킨다.
- `--`는 변수 값을 1 감소시킨다.
- `++a`는 먼저 증가시키고 값을 사용한다.
- `a++`는 먼저 값을 사용하고 나중에 증가시킨다.
- 전위 증감과 후위 증감은 다른 변수에 대입할 때 차이가 잘 보인다.
- 비교 연산자는 두 값을 비교할 때 사용한다.
- 비교 연산자의 결과는 `true` 또는 `false`이다.
- 비교 연산 결과는 `boolean` 변수에 저장할 수 있다.
- `=`는 대입이고, `==`는 비교이다.

---

## 17. 헷갈린 부분

- 전위 증감과 후위 증감의 실행 순서가 헷갈릴 수 있다.
- `++a`와 `a++`는 단독으로 보면 비슷하지만, 대입과 함께 쓰면 결과가 달라진다.
- `=`와 `==`의 차이를 계속 구분해야 한다.
- 비교 연산자의 결과가 숫자가 아니라 `boolean`이라는 점을 기억해야 한다.
- `>=`와 `<=`는 크다/작다에 같다는 조건까지 포함된다는 점을 헷갈리지 않아야 한다.

---

## 18. 내 프로젝트와 연결한 부분

- 패션 추천 시스템에서 점수를 하나씩 증가시키거나 감소시킬 때 증감 연산자를 사용할 수 있다.
- 특정 조건을 만족하면 점수를 1점 올리는 방식으로 활용할 수 있다.
- 비교 연산자는 코디 점수가 기준 이상인지 판단할 때 사용할 수 있다.
- 비교 연산 결과를 `boolean` 변수에 저장해서 추천 여부를 판단할 수 있다.

예시:

```java
int colorScore = 82;

colorScore++;

boolean isGoodColorScore = colorScore >= 80;

System.out.println(colorScore);
System.out.println(isGoodColorScore);
```

정리:

```text
colorScore        → 색상 점수
colorScore++      → 색상 점수 1 증가
isGoodColorScore  → 색상 점수가 기준 이상인지 판단
```

---

## 19. 패션 추천 시스템 예시 코드

```java
package operator;

public class FashionComparisonPractice {
    public static void main(String[] args) {
        int colorScore = 82;
        int fitScore = 78;

        colorScore++;

        boolean isColorGood = colorScore >= 80;
        boolean isFitGood = fitScore >= 80;
        boolean isSameScore = colorScore == fitScore;

        System.out.println("색상 점수: " + colorScore);
        System.out.println("핏 점수: " + fitScore);
        System.out.println("색상 점수 기준 통과: " + isColorGood);
        System.out.println("핏 점수 기준 통과: " + isFitGood);
        System.out.println("두 점수가 같은가: " + isSameScore);
    }
}
```

실행 결과:

```text
색상 점수: 83
핏 점수: 78
색상 점수 기준 통과: true
핏 점수 기준 통과: false
두 점수가 같은가: false
```

---

## 20. 오늘의 핵심 정리

- 증감 연산자는 값을 1 증가시키거나 감소시킨다.
- `++`는 1 증가이다.
- `--`는 1 감소이다.
- 전위 증감은 먼저 증가하고 사용한다.
- 후위 증감은 먼저 사용하고 증가한다.
- 비교 연산자는 두 값을 비교한다.
- 비교 연산자의 결과는 `true` 또는 `false`이다.
- 비교 결과는 `boolean` 변수에 저장할 수 있다.
- `=`는 값을 저장하는 대입 연산자이다.
- `==`는 두 값이 같은지 확인하는 비교 연산자이다.
- 오늘은 증감 연산자와 비교 연산자까지 공부했다.

---

## 21. 다음에 할 일

- 논리 연산자 공부하기
- 대입 연산자 공부하기
- 연산자 문제 풀이 정리하기
- 비교 연산자와 논리 연산자를 연결해서 이해하기
- 조건문 `if` 공부 준비하기