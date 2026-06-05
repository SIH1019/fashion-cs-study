# 2026-06-05 Java 조건문 if / else if 학습 개발일지

## 1. 오늘 공부한 주제

- 조건문
- `if`문
- `if-else`문
- `else if`문
- `else`문
- `if`문을 여러 개 사용할 때의 실행 흐름
- 독립 조건
- 배타 조건
- `if`문 중괄호 생략
- `else if`문의 조건 흐름
- switch문 전까지 학습

---

## 2. 오늘 공부한 범위

- 조건문 시작
- `if`문
- `if-else`문
- `else if`문
- `else`문
- `if`문 여러 개 사용
- `if`문 여러 개는 독립 조건이라는 점
- `else if`문은 앞 조건이 false일 때만 다음 조건을 검사한다는 점
- `if`문 중괄호 생략
- switch문 전까지

---

## 3. 오늘 공부하지 않은 범위

- switch문
- 반복문
- 배열
- 메서드
- 객체지향

---

## 4. 조건문이 필요한 이유

- 프로그램은 상황에 따라 다른 동작을 해야 할 때가 있다.
- 조건문은 특정 조건이 참인지 거짓인지 판단해서 실행할 코드를 선택할 때 사용한다.
- 조건식의 결과는 `true` 또는 `false`이다.
- 조건식이 `true`이면 해당 블록 안의 코드가 실행된다.
- 조건식이 `false`이면 해당 블록 안의 코드는 실행되지 않는다.

예시:

```java
int age = 20;

if (age >= 18) {
    System.out.println("성인입니다.");
}
```

- `age >= 18`의 결과가 `true`이면 출력문이 실행된다.
- `age >= 18`의 결과가 `false`이면 출력문이 실행되지 않는다.

---

## 5. if문

```java
if (조건식) {
    실행할 코드
}
```

- `if`문은 조건식이 참일 때만 코드를 실행한다.
- 조건식에는 비교 연산자나 논리 연산자를 사용할 수 있다.
- 조건식의 결과는 반드시 `true` 또는 `false`가 되어야 한다.
- 조건식이 `true`이면 중괄호 `{}` 안의 코드가 실행된다.
- 조건식이 `false`이면 중괄호 안의 코드는 건너뛴다.

예시:

```java
int age = 20;

if (age >= 18) {
    System.out.println("성인입니다.");
}
```

실행 결과:

```text
성인입니다.
```

풀이:

```text
age = 20
age >= 18 → true
조건이 true이므로 if 블록 실행
```

---

## 6. if문 조건이 false인 경우

```java
int age = 15;

if (age >= 18) {
    System.out.println("성인입니다.");
}

System.out.println("프로그램 종료");
```

실행 결과:

```text
프로그램 종료
```

풀이:

```text
age = 15
age >= 18 → false
if문 내부 코드 실행 안 함
다음 코드 실행
```

- `if`문 조건이 false이면 if 블록 안의 코드는 실행되지 않는다.
- 조건문이 끝난 뒤 다음 코드가 실행된다.

---

## 7. if문을 여러 개 사용할 때

```java
int age = 14;

if (age <= 7) {
    System.out.println("미취학");
}

if (age <= 13) {
    System.out.println("초등학생");
}

if (age <= 16) {
    System.out.println("중학생");
}
```

- `if`문을 여러 개 따로 쓰면 각각의 조건은 서로 독립적이다.
- 앞의 `if`문이 true였는지 false였는지와 상관없이 다음 `if`문도 검사한다.
- 즉, 모든 `if` 조건을 각각 따로 확인한다.
- 조건이 여러 개 true이면 여러 출력문이 실행될 수 있다.

예시에서 `age = 14`일 때:

```text
age <= 7   → 14 <= 7   → false
age <= 13  → 14 <= 13  → false
age <= 16  → 14 <= 16  → true
```

실행 결과:

```text
중학생
```

---

## 8. if문 여러 개는 독립 조건이다

- `if`문을 여러 개 쓰면 각각 독립적으로 검사한다.
- 위에서 한 조건이 맞았다고 해서 아래 조건 검사를 멈추지 않는다.
- 위에서 한 조건이 틀렸다고 해서 아래 조건이 자동으로 연결되는 것도 아니다.
- 각각의 `if`문은 자기 조건만 본다.

정리:

```text
if 여러 개
→ 각각 독립 조건
→ 모든 조건을 순서대로 검사
→ true인 조건은 모두 실행될 수 있음
```

예시:

```java
int score = 90;

if (score >= 60) {
    System.out.println("60점 이상");
}

if (score >= 80) {
    System.out.println("80점 이상");
}

if (score >= 90) {
    System.out.println("90점 이상");
}
```

실행 결과:

```text
60점 이상
80점 이상
90점 이상
```

- `score`가 90이므로 세 조건이 모두 true이다.
- 그래서 세 출력문이 모두 실행된다.
- 이런 경우에는 여러 조건이 동시에 실행되어도 괜찮을 때만 `if`문을 여러 개 사용해야 한다.

---

## 9. if-else문

```java
if (조건식) {
    조건이 true일 때 실행
} else {
    조건이 false일 때 실행
}
```

- `if-else`문은 조건이 참일 때와 거짓일 때 실행할 코드를 나눌 수 있다.
- `if` 조건이 true이면 `if` 블록이 실행된다.
- `if` 조건이 false이면 `else` 블록이 실행된다.
- 둘 중 하나만 실행된다.

예시:

```java
int age = 15;

if (age >= 18) {
    System.out.println("성인입니다.");
} else {
    System.out.println("미성년자입니다.");
}
```

실행 결과:

```text
미성년자입니다.
```

풀이:

```text
age = 15
age >= 18 → false
if 블록 실행 안 함
else 블록 실행
```

---

## 10. if-else문은 둘 중 하나만 실행된다

- `if-else`문은 `if` 블록과 `else` 블록 중 하나만 실행된다.
- 조건이 true이면 `if`만 실행된다.
- 조건이 false이면 `else`만 실행된다.
- 두 블록이 동시에 실행되는 경우는 없다.

정리:

```text
if 조건 true  → if 블록 실행
if 조건 false → else 블록 실행
```

---

## 11. else if문

```java
if (조건식1) {
    조건식1이 true일 때 실행
} else if (조건식2) {
    조건식1은 false이고, 조건식2가 true일 때 실행
} else {
    위 조건들이 모두 false일 때 실행
}
```

- `else if`문은 여러 조건 중 하나만 선택해서 실행할 때 사용한다.
- 위에서부터 순서대로 조건을 검사한다.
- 먼저 true가 되는 조건을 만나면 해당 블록만 실행한다.
- 한 블록이 실행되면 나머지 `else if`와 `else`는 검사하지 않는다.
- 앞 조건이 false일 때만 다음 `else if` 조건을 검사한다.

---

## 12. else if문 예제

```java
package cond;

public class If4 {
    public static void main(String[] args) {
        int age = 14;

        if (age <= 7) {
            System.out.println("미취학");
        } else if (age <= 13) {
            System.out.println("초등학생");
        } else if (age <= 16) {
            System.out.println("중학생");
        } else if (age <= 19) {
            System.out.println("고등학생");
        } else {
            System.out.println("성인");
        }
    }
}
```

실행 결과:

```text
중학생
```

풀이:

```text
age = 14

age <= 7   → 14 <= 7   → false
age <= 13  → 14 <= 13  → false
age <= 16  → 14 <= 16  → true

따라서 "중학생" 출력
```

---

## 13. else if문의 핵심 논리

- `else if`는 앞 조건이 false일 때만 검사된다.
- 그래서 코드에는 현재 조건만 적혀 있어도, 실제 의미에는 앞 조건이 false였다는 사실이 포함된다.
- 즉, `else if`는 앞 조건을 통과하지 못한 경우에만 내려오는 구조이다.

예시:

```java
if (age <= 7) {
    System.out.println("미취학");
} else if (age <= 13) {
    System.out.println("초등학생");
}
```

- `else if (age <= 13)`까지 내려왔다는 것은 이미 `age <= 7`이 false라는 뜻이다.
- 따라서 실제 의미는 아래처럼 해석할 수 있다.

```text
age > 7 && age <= 13
```

주의:

```text
age <= 7 && age <= 13
```

- 이렇게 해석하는 것은 아니다.
- `else if`는 앞 조건에 해당하지 않았을 때 내려오기 때문에, 앞 조건은 반대로 생각해야 한다.

---

## 14. 나이 조건을 실제 범위로 풀어보기

코드:

```java
if (age <= 7) {
    System.out.println("미취학");
} else if (age <= 13) {
    System.out.println("초등학생");
} else if (age <= 16) {
    System.out.println("중학생");
} else if (age <= 19) {
    System.out.println("고등학생");
} else {
    System.out.println("성인");
}
```

실제 의미:

```text
age <= 7
→ 미취학

age > 7 && age <= 13
→ 초등학생

age > 13 && age <= 16
→ 중학생

age > 16 && age <= 19
→ 고등학생

age > 19
→ 성인
```

정리:

```text
else if는 앞 조건이 false라는 전제를 가지고 다음 조건을 검사한다.
```

---

## 15. if 여러 개와 else if의 차이

### 15-1. if문 여러 개

```java
if (조건1) {
}

if (조건2) {
}

if (조건3) {
}
```

- 각각 독립적으로 검사한다.
- 조건1이 true여도 조건2, 조건3도 계속 검사한다.
- 조건이 여러 개 true이면 여러 블록이 실행될 수 있다.

정리:

```text
if 여러 개
→ 독립 조건
→ 각각 모두 검사
→ 여러 개가 실행될 수 있음
```

---

### 15-2. else if문

```java
if (조건1) {
} else if (조건2) {
} else if (조건3) {
}
```

- 위에서부터 순서대로 검사한다.
- 먼저 true가 되는 조건 하나만 실행한다.
- 하나가 실행되면 나머지는 검사하지 않는다.
- 앞 조건이 false일 때만 다음 조건으로 내려간다.

정리:

```text
else if
→ 연결 조건
→ 위에서부터 순서대로 검사
→ 하나만 실행
→ 앞 조건이 false일 때만 다음 조건 검사
```

---

## 16. 독립 조건과 배타 조건

### 16-1. 독립 조건

- 조건들이 서로 독립적으로 검사되는 구조이다.
- `if`문을 여러 개 따로 쓰는 경우가 해당된다.
- 여러 조건이 동시에 true일 수 있다.
- 여러 결과가 동시에 출력될 수 있다.

예시:

```java
if (score >= 60) {
    System.out.println("60점 이상");
}

if (score >= 80) {
    System.out.println("80점 이상");
}
```

- `score`가 90이면 두 조건이 모두 true이다.
- 그래서 두 출력문이 모두 실행될 수 있다.

---

### 16-2. 배타 조건

- 여러 조건 중 하나만 선택되어야 하는 구조이다.
- `else if`문을 사용하는 경우가 해당된다.
- 하나의 조건이 true가 되면 나머지는 실행되지 않는다.
- 나이 구간, 등급 구간처럼 하나의 결과만 나와야 할 때 사용한다.

예시:

```java
if (score >= 90) {
    System.out.println("A");
} else if (score >= 80) {
    System.out.println("B");
} else if (score >= 70) {
    System.out.println("C");
}
```

- `score`가 95이면 `A`만 출력된다.
- `B`, `C` 조건은 검사하지 않는다.

---

## 17. if문 중괄호 생략

- `if`문에서 실행할 문장이 한 줄이면 중괄호 `{}`를 생략할 수 있다.
- 하지만 중괄호를 생략하면 바로 아래 한 문장만 `if`문에 포함된다.
- 그 다음 줄부터는 `if`문과 상관없이 항상 실행된다.
- 그래서 초보 단계에서는 중괄호를 생략하지 않는 것이 좋다.

예시:

```java
int age = 20;

if (age >= 18)
    System.out.println("성인입니다.");
```

실행 결과:

```text
성인입니다.
```

- 조건이 true이므로 바로 아래 출력문이 실행된다.
- 이 경우에는 문장이 한 줄이라 중괄호 생략이 가능하다.

---

## 18. 중괄호 생략 시 주의점

```java
int age = 15;

if (age >= 18)
    System.out.println("성인입니다.");
    System.out.println("입장 가능합니다.");
```

실행 결과:

```text
입장 가능합니다.
```

풀이:

```text
age = 15
age >= 18 → false

System.out.println("성인입니다.");
→ if문에 포함된 한 줄이므로 실행 안 됨

System.out.println("입장 가능합니다.");
→ if문에 포함되지 않은 코드이므로 항상 실행됨
```

- 중괄호가 없으면 `if`문 바로 아래 한 줄만 조건문에 포함된다.
- 들여쓰기가 되어 있어도 Java는 들여쓰기로 범위를 판단하지 않는다.
- Java는 중괄호 `{}`로 코드의 범위를 판단한다.

---

## 19. 중괄호를 사용하는 것이 좋은 이유

```java
int age = 15;

if (age >= 18) {
    System.out.println("성인입니다.");
    System.out.println("입장 가능합니다.");
}
```

- 중괄호를 사용하면 여러 문장을 하나의 블록으로 묶을 수 있다.
- 조건이 true일 때 실행할 코드 범위가 명확해진다.
- 실수를 줄일 수 있다.
- 나중에 코드를 수정할 때 안전하다.

정리:

```text
중괄호 생략 가능
→ 실행 문장이 한 줄일 때만 가능
→ 하지만 헷갈릴 수 있음
→ 항상 중괄호를 쓰는 습관이 좋음
```

---

## 20. else if를 쓰면 좋은 경우

- 여러 조건 중 하나의 결과만 선택하고 싶을 때 사용한다.
- 조건을 위에서부터 순서대로 검사할 수 있다.
- 먼저 만족하는 조건이 있으면 그 결과만 실행된다.
- 나머지 조건은 검사하지 않아 불필요한 검사를 줄일 수 있다.
- 범위를 나누는 코드에서 자주 사용한다.

예시:

```text
나이 구간 분류
점수 등급 분류
가격 구간 분류
권한 단계 분류
패션 점수 구간 분류
```

---

## 21. else문

```java
else {
    System.out.println("성인");
}
```

- `else`는 위의 모든 조건이 false일 때 실행된다.
- 조건식을 따로 쓰지 않는다.
- 마지막 기본값처럼 사용할 수 있다.

예시:

```java
if (age <= 7) {
    System.out.println("미취학");
} else if (age <= 13) {
    System.out.println("초등학생");
} else if (age <= 16) {
    System.out.println("중학생");
} else if (age <= 19) {
    System.out.println("고등학생");
} else {
    System.out.println("성인");
}
```

- `age`가 20 이상이면 위 조건들이 모두 false가 된다.
- 그래서 마지막 `else`가 실행된다.
- 결과는 `성인`이다.

---

## 22. 오늘 작성한 예제 코드

```java
package cond;

public class If4 {
    public static void main(String[] args) {
        int age = 14;

        if (age <= 7) {
            System.out.println("미취학");
        } else if (age <= 13) {
            System.out.println("초등학생");
        } else if (age <= 16) {
            System.out.println("중학생");
        } else if (age <= 19) {
            System.out.println("고등학생");
        } else {
            System.out.println("성인");
        }
    }
}
```

실행 결과:

```text
중학생
```

---

## 23. 오늘 새로 알게 된 점

- 조건문은 조건에 따라 실행할 코드를 선택할 때 사용한다.
- `if`문은 조건이 true일 때만 실행된다.
- `if`문을 여러 개 쓰면 각각 독립 조건으로 검사된다.
- 독립 조건에서는 여러 조건이 true이면 여러 블록이 실행될 수 있다.
- `if-else`문은 true일 때와 false일 때 실행할 코드를 나눌 수 있다.
- `else if`문은 여러 조건 중 하나만 선택할 때 사용한다.
- `else if`는 앞 조건이 false일 때만 검사된다.
- `else if`까지 내려왔다는 것은 앞 조건에 해당하지 않았다는 뜻이다.
- 그래서 `else if (age <= 13)`은 실제로 `age > 7 && age <= 13`처럼 해석할 수 있다.
- 단, 코드에 조건이 자동으로 합쳐지는 것이 아니라 실행 흐름상 그렇게 해석되는 것이다.
- `if`문에서 실행할 문장이 한 줄이면 중괄호를 생략할 수 있다.
- 하지만 중괄호를 생략하면 바로 아래 한 문장만 `if`문에 포함된다.
- Java는 들여쓰기가 아니라 중괄호로 코드 범위를 판단한다.
- `else`는 위 조건이 모두 false일 때 실행된다.

---

## 24. 헷갈린 부분

- `if`문 여러 개와 `else if`문의 차이가 헷갈릴 수 있다.
- `if`문 여러 개는 각각 독립 조건이라 모든 조건을 검사한다.
- `else if`문은 앞 조건이 false일 때만 다음 조건을 검사한다.
- `else if (age <= 13)`이 단순히 `age <= 13`만 보는 것처럼 보이지만, 실제로는 앞 조건이 false인 상태에서 검사된다는 점을 이해해야 한다.
- `age <= 7 && age <= 13`처럼 합쳐지는 것이 아니라, `age > 7 && age <= 13`처럼 해석해야 한다.
- 중괄호를 생략하면 여러 줄이 조건문에 포함되는 것처럼 보일 수 있지만 실제로는 바로 아래 한 줄만 포함된다.
- 들여쓰기가 되어 있어도 중괄호가 없으면 조건문 범위가 달라질 수 있다.
- 여러 조건 중 하나만 실행하고 싶을 때는 `else if`를 사용하는 것이 좋다.

---

## 25. 내 프로젝트와 연결한 부분

- 패션 추천 시스템에서 점수 구간을 나눌 때 `else if`문을 사용할 수 있다.
- 전체 점수에 따라 코디 평가를 다르게 출력할 수 있다.
- 예를 들어 점수가 높으면 추천, 중간이면 보완 필요, 낮으면 비추천으로 나눌 수 있다.
- `else if`를 사용하면 여러 점수 구간 중 하나의 결과만 출력할 수 있다.
- 반대로 여러 조건을 동시에 검사해야 할 때는 `if`문을 여러 개 사용할 수 있다.
- 조건문 안에서 여러 문장을 실행해야 한다면 중괄호를 반드시 사용하는 것이 안전하다.

예시:

```java
int totalScore = 82;

if (totalScore >= 90) {
    System.out.println("매우 추천");
} else if (totalScore >= 70) {
    System.out.println("추천");
} else if (totalScore >= 50) {
    System.out.println("보완 필요");
} else {
    System.out.println("비추천");
}
```

실제 의미:

```text
totalScore >= 90
→ 매우 추천

totalScore < 90 && totalScore >= 70
→ 추천

totalScore < 70 && totalScore >= 50
→ 보완 필요

totalScore < 50
→ 비추천
```

---

## 26. 패션 추천 시스템 예시 코드

```java
package cond;

public class FashionScoreCondition {
    public static void main(String[] args) {
        int totalScore = 82;

        if (totalScore >= 90) {
            System.out.println("매우 추천");
        } else if (totalScore >= 70) {
            System.out.println("추천");
        } else if (totalScore >= 50) {
            System.out.println("보완 필요");
        } else {
            System.out.println("비추천");
        }
    }
}
```

실행 결과:

```text
추천
```

풀이:

```text
totalScore = 82

totalScore >= 90 → false
totalScore >= 70 → true

따라서 "추천" 출력
```

---

## 27. 오늘의 핵심 정리

- 조건문은 조건에 따라 실행 흐름을 나누는 문법이다.
- `if`문은 조건이 true일 때만 실행된다.
- `if`문을 여러 개 쓰면 각각 독립 조건으로 모두 검사한다.
- `if-else`문은 조건이 true일 때와 false일 때를 나눌 수 있다.
- `else if`문은 여러 조건 중 하나만 선택해서 실행할 때 사용한다.
- `else if`는 앞 조건이 false일 때만 다음 조건을 검사한다.
- 그래서 `else if` 조건은 앞 조건의 반대 조건을 깔고 들어간다고 이해할 수 있다.
- `if`문에서 실행 문장이 한 줄이면 중괄호를 생략할 수 있다.
- 하지만 중괄호를 생략하면 바로 아래 한 줄만 조건문에 포함된다.
- Java는 들여쓰기가 아니라 중괄호로 코드 범위를 판단한다.
- 초보 단계에서는 중괄호를 항상 쓰는 것이 안전하다.
- `else`는 위 조건이 모두 false일 때 실행된다.
- 하나만 선택해야 하는 구간 분류에는 `else if`가 적합하다.
- 여러 조건을 동시에 검사해야 하면 `if`문을 여러 개 사용할 수 있다.
- 오늘은 switch문 전까지 공부했다.

---

## 28. 다음에 할 일

- switch문 공부하기
- switch문과 if문의 차이 이해하기
- 조건문 문제 풀이 정리하기
- 패션 추천 시스템에서 점수 구간별 결과 출력 코드 작성하기