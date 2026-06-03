# 2026-06-03 Java 논리 연산자 및 연산자 정리 개발일지

## 1. 오늘 공부한 주제

- 논리 연산자
- 대입 연산자
- 복합 대입 연산자
- 연산자 우선순위 복습
- 연산자 단원 최종 정리

---

## 2. 오늘 공부한 범위

- 논리 연산자
- `&&`
- `||`
- `!`
- 대입 연산자
- 복합 대입 연산자
- 연산자 우선순위 정리
- 연산자 전체 핵심 정리

---

## 3. 오늘 공부하지 않은 범위

- 조건문
- 반복문
- 메서드
- 배열
- 객체지향

---

## 4. 논리 연산자

- 논리 연산자는 여러 조건을 함께 판단할 때 사용한다.
- 비교 연산자의 결과인 `true`, `false`를 조합할 수 있다.
- 조건이 여러 개일 때 전체 결과를 판단하는 데 사용한다.
- 결과는 항상 `true` 또는 `false`이다.

정리:

```text
&&  → 그리고
||  → 또는
!   → 부정
```

---

## 5. `&&` 연산자

- `&&`는 AND 연산자이다.
- 양쪽 조건이 모두 참일 때만 결과가 `true`이다.
- 하나라도 거짓이면 결과는 `false`이다.

예시:

```java
int age = 22;
boolean isStudent = true;

System.out.println(age >= 20 && isStudent);
```

실행 결과:

```text
true
```

풀이:

```text
age >= 20      → true
isStudent      → true
true && true   → true
```

정리:

```text
true && true   → true
true && false  → false
false && true  → false
false && false → false
```

---

## 6. `||` 연산자

- `||`는 OR 연산자이다.
- 양쪽 조건 중 하나라도 참이면 결과가 `true`이다.
- 둘 다 거짓일 때만 결과가 `false`이다.

예시:

```java
int age = 17;
boolean hasPermission = true;

System.out.println(age >= 20 || hasPermission);
```

실행 결과:

```text
true
```

풀이:

```text
age >= 20          → false
hasPermission      → true
false || true      → true
```

정리:

```text
true || true   → true
true || false  → true
false || true  → true
false || false → false
```

---

## 7. `!` 연산자

- `!`는 NOT 연산자이다.
- 현재 값을 반대로 바꾼다.
- `true`는 `false`가 된다.
- `false`는 `true`가 된다.

예시:

```java
boolean isMatched = true;

System.out.println(!isMatched);
```

실행 결과:

```text
false
```

정리:

```text
!true  → false
!false → true
```

---

## 8. 논리 연산자 사용 예시

```java
int score = 85;
boolean isColorMatched = true;

boolean isRecommended = score >= 80 && isColorMatched;

System.out.println(isRecommended);
```

실행 결과:

```text
true
```

풀이:

```text
score >= 80       → true
isColorMatched    → true
true && true      → true
```

- 점수가 기준 이상이고 색상 조합도 적절하면 추천 가능하다고 판단할 수 있다.
- 이런 방식으로 여러 조건을 함께 검사할 수 있다.

---

## 9. 대입 연산자

- 대입 연산자는 오른쪽 값을 왼쪽 변수에 저장할 때 사용한다.
- `=`는 같다는 뜻이 아니라 값을 저장한다는 뜻이다.

예시:

```java
int a = 10;
```

풀이:

```text
10을 변수 a에 저장
```

정리:

```text
=  → 오른쪽 값을 왼쪽 변수에 저장
```

---

## 10. 대입 연산자와 비교 연산자 차이

```java
int a = 10;
System.out.println(a == 10);
```

- `=`는 값을 저장할 때 사용한다.
- `==`는 두 값이 같은지 비교할 때 사용한다.

정리:

```text
=   → 대입
==  → 비교
```

- `a = 10`
  - `a`에 `10`을 저장한다.

- `a == 10`
  - `a`의 값이 `10`과 같은지 비교한다.

---

## 11. 복합 대입 연산자

- 복합 대입 연산자는 연산과 대입을 한 번에 처리한다.
- 기존 변수 값에 계산을 적용한 뒤 다시 같은 변수에 저장한다.

정리:

```text
a += 3  → a = a + 3
a -= 3  → a = a - 3
a *= 3  → a = a * 3
a /= 3  → a = a / 3
a %= 3  → a = a % 3
```

---

## 12. 복합 대입 연산자 예시

```java
int a = 10;

a += 3;
System.out.println(a);
```

실행 결과:

```text
13
```

풀이:

```text
a += 3
→ a = a + 3
→ a = 10 + 3
→ a = 13
```

---

## 13. 복합 대입 연산자 종류

### 13-1. `+=`

```java
int a = 10;
a += 5;
```

정리:

```text
a = a + 5
```

---

### 13-2. `-=`

```java
int a = 10;
a -= 5;
```

정리:

```text
a = a - 5
```

---

### 13-3. `*=`

```java
int a = 10;
a *= 5;
```

정리:

```text
a = a * 5
```

---

### 13-4. `/=`

```java
int a = 10;
a /= 5;
```

정리:

```text
a = a / 5
```

---

### 13-5. `%=`

```java
int a = 10;
a %= 3;
```

정리:

```text
a = a % 3
```

---

## 14. 연산자 우선순위 복습

- 연산자 우선순위는 여러 연산자가 함께 있을 때 어떤 연산을 먼저 할지 정하는 규칙이다.
- 모든 우선순위를 외우기보다 헷갈리면 괄호를 사용하는 것이 좋다.
- 괄호를 사용하면 계산 순서가 명확해진다.

예시:

```java
int result = 2 + 3 * 4;
System.out.println(result);
```

실행 결과:

```text
14
```

풀이:

```text
3 * 4 먼저 계산
2 + 12 계산
결과 14
```

---

## 15. 괄호 사용 예시

```java
int result = (2 + 3) * 4;
System.out.println(result);
```

실행 결과:

```text
20
```

풀이:

```text
2 + 3 먼저 계산
5 * 4 계산
결과 20
```

- 괄호를 사용하면 원하는 계산 순서를 직접 지정할 수 있다.

---

## 16. 자주 보는 연산자 우선순위

```text
1. 괄호 ()
2. 증감 연산자 ++, --
3. 곱셈 / 나눗셈 / 나머지 *, /, %
4. 덧셈 / 뺄셈 +, -
5. 비교 연산자 <, <=, >, >=, ==, !=
6. 논리 연산자 &&, ||
7. 대입 연산자 =
```

- 대입 연산자는 보통 가장 나중에 처리된다.
- 비교 연산 결과는 `true` 또는 `false`이다.
- 논리 연산자는 비교 결과들을 조합한다.

---

## 17. 오늘 작성한 예제 코드

```java
package operator;

public class LogicalAssignmentPractice {
    public static void main(String[] args) {
        int score = 85;
        boolean isColorMatched = true;

        boolean isHighScore = score >= 80;
        boolean isRecommended = isHighScore && isColorMatched;

        System.out.println(isHighScore);
        System.out.println(isRecommended);
        System.out.println(!isRecommended);

        int colorScore = 80;

        colorScore += 5;
        System.out.println(colorScore);

        colorScore -= 3;
        System.out.println(colorScore);

        colorScore *= 2;
        System.out.println(colorScore);

        colorScore /= 2;
        System.out.println(colorScore);

        colorScore %= 10;
        System.out.println(colorScore);
    }
}
```

실행 결과:

```text
true
true
false
85
82
164
82
2
```

---

## 18. 오늘 새로 알게 된 점

- 논리 연산자는 여러 조건을 함께 판단할 때 사용한다.
- `&&`는 양쪽이 모두 참일 때만 `true`이다.
- `||`는 하나라도 참이면 `true`이다.
- `!`는 결과를 반대로 바꾼다.
- 논리 연산의 결과도 `true` 또는 `false`이다.
- 대입 연산자 `=`는 오른쪽 값을 왼쪽 변수에 저장한다.
- 복합 대입 연산자는 연산과 대입을 한 번에 처리한다.
- `a += 3`은 `a = a + 3`과 같은 의미이다.
- 연산자 우선순위가 헷갈리면 괄호를 사용하는 것이 좋다.

---

## 19. 헷갈린 부분

- `&&`와 `||`의 차이가 헷갈릴 수 있다.
- `!`가 값을 반대로 바꾸는 점을 기억해야 한다.
- `=`는 대입이고 `==`는 비교라는 점을 계속 구분해야 한다.
- 복합 대입 연산자는 짧게 쓰지만 내부적으로는 기존 값에 연산 후 다시 저장하는 구조이다.
- 연산자 우선순위를 외우기보다 괄호로 명확하게 쓰는 것이 좋다고 느꼈다.

---

## 20. 내 프로젝트와 연결한 부분

- 패션 추천 시스템에서 여러 조건을 동시에 판단할 때 논리 연산자를 사용할 수 있다.
- 색상 점수가 기준 이상이고, 핏 점수도 기준 이상이면 추천 가능한 코디로 판단할 수 있다.
- 특정 조건을 만족하면 점수를 더할 때 복합 대입 연산자를 사용할 수 있다.
- 조건이 많아질수록 괄호를 사용해서 판단 순서를 명확하게 해야 한다.

예시:

```java
int colorScore = 82;
int fitScore = 78;

boolean isColorGood = colorScore >= 80;
boolean isFitGood = fitScore >= 75;

boolean isRecommended = isColorGood && isFitGood;

System.out.println(isRecommended);
```

정리:

```text
colorScore     → 색상 점수
fitScore       → 핏 점수
isColorGood    → 색상 점수가 기준 이상인지 판단
isFitGood      → 핏 점수가 기준 이상인지 판단
isRecommended  → 추천 가능한 코디인지 최종 판단
```

---

## 21. 패션 추천 시스템 예시 코드

```java
package operator;

public class FashionLogicalPractice {
    public static void main(String[] args) {
        int colorScore = 82;
        int fitScore = 78;
        int lengthScore = 75;

        boolean isColorGood = colorScore >= 80;
        boolean isFitGood = fitScore >= 75;
        boolean isLengthGood = lengthScore >= 70;

        boolean isRecommended = isColorGood && isFitGood && isLengthGood;

        System.out.println("색상 점수 통과: " + isColorGood);
        System.out.println("핏 점수 통과: " + isFitGood);
        System.out.println("기장 점수 통과: " + isLengthGood);
        System.out.println("추천 가능 여부: " + isRecommended);

        colorScore += 3;
        fitScore += 2;

        System.out.println("수정 후 색상 점수: " + colorScore);
        System.out.println("수정 후 핏 점수: " + fitScore);
    }
}
```

실행 결과:

```text
색상 점수 통과: true
핏 점수 통과: true
기장 점수 통과: true
추천 가능 여부: true
수정 후 색상 점수: 85
수정 후 핏 점수: 80
```

---

## 22. 연산자 단원 핵심 정리

- 산술 연산자는 숫자 계산에 사용한다.
- 문자열과 `+`를 사용하면 문자열 연결이 된다.
- 증감 연산자는 값을 1 증가하거나 감소시킨다.
- 비교 연산자는 두 값을 비교하고 결과는 `boolean`이다.
- 논리 연산자는 여러 조건을 함께 판단한다.
- 대입 연산자는 값을 변수에 저장한다.
- 복합 대입 연산자는 연산과 대입을 한 번에 처리한다.
- 연산자 우선순위는 계산 순서를 정한다.
- 헷갈리는 연산식은 괄호를 사용하면 된다.

---

## 23. 오늘의 핵심 정리

- 오늘은 논리 연산자부터 연산자 단원 정리까지 공부했다.
- `&&`는 모든 조건이 참일 때만 `true`이다.
- `||`는 하나라도 참이면 `true`이다.
- `!`는 참과 거짓을 반대로 바꾼다.
- `=`는 값을 저장하는 대입 연산자이다.
- `+=`, `-=`, `*=`, `/=`, `%=`는 복합 대입 연산자이다.
- 비교 연산과 논리 연산을 함께 사용하면 여러 조건을 동시에 판단할 수 있다.
- 패션 추천 시스템에서는 점수 기준과 추천 여부 판단에 논리 연산자를 사용할 수 있다.

---

## 24. 다음에 할 일

- 연산자 문제 다시 풀어보기
- 조건문 `if` 공부 시작하기
- 비교 연산자와 논리 연산자를 조건문에 연결해서 이해하기
- 패션 추천 시스템에서 점수 기준으로 추천 여부를 판단하는 코드 작성하기