# 2026-06-06 Java switch문, 삼항 연산자, 조건문 문제 풀이 개발일지

## 1. 오늘 공부한 주제

- `switch`문
- `case`
- `break`
- `default`
- `switch`문 실행 흐름
- `switch`문에서 `break`가 필요한 이유
- `if문`과 `switch문`의 차이
- 삼항 연산자
- 조건문 문제 풀이
- 조건문 단원 정리

---

## 2. 오늘 공부한 범위

- `switch`문
- `switch`문 기본 구조
- `case` 사용법
- `break` 사용법
- `default` 사용법
- `break`가 없을 때 실행 흐름
- 여러 `case`를 같은 결과로 처리하는 방식
- `if문`과 `switch문` 비교
- 삼항 연산자
- 조건문 문제 풀이
- 조건문 단원 정리

---

## 3. 오늘 공부하지 않은 범위

- 반복문
- 배열
- 메서드
- 객체지향
- 클래스 설계

---

## 4. switch문이 필요한 이유

- `switch`문은 하나의 값에 따라 실행할 코드를 나눌 때 사용한다.
- 여러 값 중 어떤 값인지 비교해서 알맞은 코드를 실행한다.
- `if-else if`문으로도 작성할 수 있지만, 특정 값 하나를 기준으로 여러 경우를 나눌 때는 `switch`문이 더 깔끔할 수 있다.
- 등급, 메뉴 번호, 월, 상태값처럼 정해진 값 중 하나를 고를 때 사용하기 좋다.

예시 상황:

```text
grade가 1이면 VIP
grade가 2이면 GOLD
grade가 3이면 SILVER
그 외는 BASIC
```

---

## 5. switch문 기본 구조

```java
switch (조건값) {
    case 값1:
        실행할 코드
        break;
    case 값2:
        실행할 코드
        break;
    default:
        실행할 코드
}
```

- `switch` 괄호 안에는 비교할 값을 넣는다.
- `case`에는 비교할 대상 값을 적는다.
- `조건값`과 `case` 값이 같으면 해당 코드가 실행된다.
- `break`를 만나면 `switch`문을 빠져나간다.
- `default`는 맞는 `case`가 없을 때 실행된다.

---

## 6. switch문 예제

```java
package cond;

public class Switch1 {
    public static void main(String[] args) {
        int grade = 2;

        switch (grade) {
            case 1:
                System.out.println("VIP");
                break;
            case 2:
                System.out.println("GOLD");
                break;
            case 3:
                System.out.println("SILVER");
                break;
            default:
                System.out.println("BASIC");
        }
    }
}
```

실행 결과:

```text
GOLD
```

풀이:

```text
grade = 2

case 1 → grade와 다름 → 실행 안 함
case 2 → grade와 같음 → "GOLD" 출력
break  → switch문 종료
```

---

## 7. case

- `case`는 `switch`문에서 비교할 값을 나타낸다.
- `switch` 괄호 안의 값과 `case` 값이 같으면 해당 코드가 실행된다.
- `case`는 여러 개 작성할 수 있다.
- 각 `case`마다 실행할 코드를 다르게 작성할 수 있다.

정리:

```text
case 값:
→ switch 값과 같은 경우 실행되는 위치
```

---

## 8. break

- `break`는 `switch`문을 빠져나갈 때 사용한다.
- 해당 `case`의 코드를 실행한 뒤 `break`를 만나면 `switch`문이 종료된다.
- `break`가 없으면 다음 `case` 코드까지 이어서 실행될 수 있다.
- 초보 단계에서는 각 `case` 끝에 `break`를 넣는 습관이 좋다.

정리:

```text
break
→ 현재 case 실행 후 switch문 종료
```

---

## 9. default

- `default`는 일치하는 `case`가 없을 때 실행된다.
- `if-else if`문의 마지막 `else`와 비슷한 역할을 한다.
- 모든 경우에 해당하지 않을 때 기본 실행 코드를 작성할 수 있다.

정리:

```text
default
→ 일치하는 case가 없을 때 실행
→ if문의 else와 비슷한 역할
```

---

## 10. break가 없을 때 실행 흐름

```java
package cond;

public class Switch2 {
    public static void main(String[] args) {
        int grade = 2;

        switch (grade) {
            case 1:
                System.out.println("VIP");
            case 2:
                System.out.println("GOLD");
            case 3:
                System.out.println("SILVER");
            default:
                System.out.println("BASIC");
        }
    }
}
```

실행 결과:

```text
GOLD
SILVER
BASIC
```

풀이:

```text
grade = 2

case 1 → 일치하지 않음
case 2 → 일치함 → "GOLD" 출력
break 없음
case 3 → 이어서 실행 → "SILVER" 출력
break 없음
default → 이어서 실행 → "BASIC" 출력
```

정리:

```text
break 있음
→ 해당 case만 실행하고 switch문 종료

break 없음
→ 일치한 case부터 아래 코드까지 계속 실행
```

---

## 11. 여러 case를 같은 결과로 처리하기

- 여러 값이 같은 결과를 가져야 할 때 `case`를 연속해서 사용할 수 있다.
- 중간에 `break`를 넣지 않고 같은 실행 코드로 내려가게 만들 수 있다.
- 의도적으로 `break`를 생략해서 여러 `case`를 하나의 결과로 묶는 방식이다.

예시:

```java
package cond;

public class Switch3 {
    public static void main(String[] args) {
        int grade = 2;

        switch (grade) {
            case 1:
            case 2:
                System.out.println("우수 회원");
                break;
            case 3:
                System.out.println("일반 회원");
                break;
            default:
                System.out.println("손님");
        }
    }
}
```

실행 결과:

```text
우수 회원
```

풀이:

```text
grade = 2

case 1 → 일치하지 않음
case 2 → 일치함
"우수 회원" 출력
break → switch문 종료
```

---

## 12. if문과 switch문의 차이

### 12-1. if문

- 조건식이 자유롭다.
- 범위 비교가 가능하다.
- 비교 연산자와 논리 연산자를 사용할 수 있다.
- 복잡한 조건을 표현하기 좋다.

예시:

```java
if (score >= 90) {
    System.out.println("A");
} else if (score >= 80) {
    System.out.println("B");
}
```

- `score >= 90`
- `score >= 80`

처럼 범위 조건을 사용할 수 있다.

---

### 12-2. switch문

- 하나의 값이 어떤 값과 같은지 비교할 때 사용하기 좋다.
- 정해진 값 중 하나를 선택하는 구조에 적합하다.
- 범위 비교에는 적합하지 않다.
- `case` 값과 일치하는지 확인한다.

예시:

```java
switch (grade) {
    case 1:
        System.out.println("VIP");
        break;
    case 2:
        System.out.println("GOLD");
        break;
}
```

- `grade`가 `1`인지
- `grade`가 `2`인지

처럼 특정 값과 일치하는지를 확인한다.

---

## 13. if문과 switch문 선택 기준

```text
범위 조건이 필요함
→ if문 사용

복잡한 조건이 필요함
→ if문 사용

하나의 값이 여러 값 중 무엇인지 비교함
→ switch문 사용

메뉴 번호, 등급, 월, 상태값처럼 정해진 값 비교
→ switch문 사용
```

예시:

```text
나이가 20 이상인지 판단
→ if문

점수가 90 이상인지 판단
→ if문

메뉴 번호가 1, 2, 3 중 무엇인지 판단
→ switch문

회원 등급이 1, 2, 3 중 무엇인지 판단
→ switch문
```

---

## 14. 삼항 연산자

- 삼항 연산자는 조건에 따라 값을 선택할 때 사용하는 연산자이다.
- `if-else`문을 짧게 표현할 수 있다.
- 조건에 따라 단순히 하나의 값을 선택할 때 사용하기 좋다.
- 구조는 `조건식 ? 참일 때 값 : 거짓일 때 값`이다.

기본 구조:

```java
조건식 ? true일 때 값 : false일 때 값
```

---

## 15. 삼항 연산자 예제

```java
package cond;

public class CondOp1 {
    public static void main(String[] args) {
        int age = 18;

        String status = age >= 18 ? "성인" : "미성년자";

        System.out.println(status);
    }
}
```

실행 결과:

```text
성인
```

풀이:

```text
age = 18
age >= 18 → true
true이면 "성인" 선택
status에 "성인" 저장
```

---

## 16. if-else문과 삼항 연산자 비교

### 16-1. if-else문

```java
int age = 18;
String status;

if (age >= 18) {
    status = "성인";
} else {
    status = "미성년자";
}

System.out.println(status);
```

- 조건에 따라 `status`에 값을 저장한다.
- 코드가 여러 줄이다.
- 실행할 코드가 많으면 `if-else`문이 더 적합하다.

---

### 16-2. 삼항 연산자

```java
int age = 18;

String status = age >= 18 ? "성인" : "미성년자";

System.out.println(status);
```

- 조건에 따라 하나의 값을 선택한다.
- 코드가 짧다.
- 단순한 값 선택에는 삼항 연산자가 깔끔하다.

정리:

```text
if-else문
→ 실행할 코드가 여러 줄이거나 복잡할 때 사용

삼항 연산자
→ 조건에 따라 하나의 값을 선택할 때 사용
```

---

## 17. 삼항 연산자 사용 시 주의점

- 삼항 연산자는 너무 복잡하게 쓰면 오히려 읽기 어렵다.
- 조건이 단순할 때만 사용하는 것이 좋다.
- 실행할 코드가 여러 줄이면 삼항 연산자보다 `if-else`문이 적합하다.
- 삼항 연산자는 값을 선택하는 데 초점이 있다.

정리:

```text
단순 값 선택
→ 삼항 연산자 가능

복잡한 조건 처리
→ if-else문 사용
```

---

## 18. 문제 풀이 1: 환율 계산

### 18-1. 문제 내용

- 달러 금액을 원화로 환전한다.
- `dollar`가 0보다 작으면 잘못된 금액을 출력한다.
- `dollar`가 0이면 환전할 금액이 없다고 출력한다.
- `dollar`가 0보다 크면 `dollar * 1400` 값을 출력한다.

---

### 18-2. 작성 코드

```java
package cond.ex;

public class ExchangeRateEx {
    public static void main(String[] args) {
        int dollar = 3;

        if (dollar < 0) {
            System.out.println("잘못된 금액");
        } else if (dollar == 0) {
            System.out.println("환전할 금액이 없음");
        } else {
            System.out.println("환전 금액은 " + dollar * 1400 + "원 입니다");
        }
    }
}
```

---

### 18-3. 실행 결과

```text
환전 금액은 4200원 입니다
```

---

### 18-4. 풀이 정리

- `dollar = 3`이다.
- `dollar < 0`은 false이다.
- `dollar == 0`도 false이다.
- 앞 조건들이 모두 false이므로 `else`로 내려간다.
- `dollar * 1400`을 계산한다.
- `3 * 1400 = 4200`이다.
- 최종 출력은 `환전 금액은 4200원 입니다`이다.

정리:

```text
dollar < 0
→ 잘못된 금액

dollar == 0
→ 환전할 금액이 없음

dollar > 0
→ 환전 금액 계산
```

---

## 19. 문제 풀이 2: 평점에 따른 영화 추천

### 19-1. 문제 내용

- `rating` 값에 따라 추천 영화를 출력한다.
- 평점이 9점 이상이면 `어바웃타임`을 추천한다.
- 평점이 8점 이상이면 `토이 스토리`를 추천한다.
- 평점이 7점 이상이면 `고질라`를 추천한다.
- 여러 `if`문을 사용하면 조건을 만족하는 추천이 여러 개 출력될 수 있다.

---

### 19-2. 작성 코드

```java
package cond.ex;

public class MovieRateEx {
    public static void main(String[] args) {
        double rating = 8.5;

        if (rating >= 9) {
            System.out.println("어바웃타임을 추천합니다.");
        }

        if (rating >= 8) {
            System.out.println("토이 스토리를 추천합니다.");
        }

        if (rating >= 7) {
            System.out.println("고질라를 추천합니다.");
        }
    }
}
```

---

### 19-3. 실행 결과

```text
토이 스토리를 추천합니다.
고질라를 추천합니다.
```

---

### 19-4. 풀이 정리

- `rating = 8.5`이다.
- `rating >= 9`는 false이다.
- `rating >= 8`은 true이므로 `토이 스토리`가 출력된다.
- `rating >= 7`도 true이므로 `고질라`가 출력된다.
- `if`문을 여러 개 사용했기 때문에 각 조건이 독립적으로 검사된다.
- 조건을 만족하는 결과가 여러 개 출력된다.

정리:

```text
if 여러 개
→ 독립 조건
→ 조건을 각각 검사
→ 여러 결과가 출력될 수 있음
```

---

## 20. 문제 풀이 3: 학점 출력

### 20-1. 문제 내용

- `score` 점수에 따라 학점을 출력한다.
- 90점 이상이면 `A`
- 80점 이상이면 `B`
- 70점 이상이면 `C`
- 60점 이상이면 `D`
- 나머지는 `F`

---

### 20-2. 작성 코드

```java
package cond.ex;

public class ScoreEx {
    public static void main(String[] args) {
        int score = 85;

        if (score >= 90) {
            System.out.println("A");
        } else if (score >= 80) {
            System.out.println("B");
        } else if (score >= 70) {
            System.out.println("C");
        } else if (score >= 60) {
            System.out.println("D");
        } else {
            System.out.println("F");
        }
    }
}
```

---

### 20-3. 실행 결과

```text
B
```

---

### 20-4. 풀이 정리

- `score = 85`이다.
- `score >= 90`은 false이다.
- `score >= 80`은 true이다.
- 따라서 `B`가 출력된다.
- `else if`문은 하나가 실행되면 나머지 조건은 검사하지 않는다.
- 점수 구간처럼 하나만 선택해야 하는 경우 `else if`문이 적합하다.

정리:

```text
score >= 90
→ A

score < 90 && score >= 80
→ B

score < 80 && score >= 70
→ C

score < 70 && score >= 60
→ D

score < 60
→ F
```

---

## 21. 문제 풀이 4: 거리에 따른 이동 수단 선택

### 21-1. 문제 내용

- `distance` 값에 따라 이동 수단을 출력한다.
- 거리가 1 이하이면 도보
- 거리가 10 이하이면 자전거
- 거리가 100 이하이면 자동차
- 그 외는 비행기

---

### 21-2. 작성 코드

```java
package cond.ex;

public class DistanceEx {
    public static void main(String[] args) {
        int distance = 25;

        if (distance <= 1) {
            System.out.println("도보");
        } else if (distance <= 10) {
            System.out.println("자전거");
        } else if (distance <= 100) {
            System.out.println("자동차");
        } else {
            System.out.println("비행기");
        }
    }
}
```

---

### 21-3. 실행 결과

```text
자동차
```

---

### 21-4. 풀이 정리

- `distance = 25`이다.
- `distance <= 1`은 false이다.
- `distance <= 10`도 false이다.
- `distance <= 100`은 true이다.
- 따라서 `자동차`가 출력된다.
- `else if`문은 앞 조건이 false일 때만 다음 조건을 검사한다.

정리:

```text
distance <= 1
→ 도보

distance > 1 && distance <= 10
→ 자전거

distance > 10 && distance <= 100
→ 자동차

distance > 100
→ 비행기
```

---

## 22. 조건문 전체 정리

- 조건문은 조건에 따라 실행 흐름을 나누는 문법이다.
- Java 조건문에는 대표적으로 `if문`, `switch문`, 삼항 연산자가 있다.
- `if문`은 조건식이 `true`일 때 코드를 실행한다.
- `if-else문`은 조건이 참일 때와 거짓일 때를 나눌 수 있다.
- `else if문`은 여러 조건 중 하나만 선택할 때 사용한다.
- `else문`은 위 조건들이 모두 false일 때 실행된다.
- `switch문`은 하나의 값이 어떤 값과 일치하는지에 따라 실행 흐름을 나눌 때 사용한다.
- 삼항 연산자는 조건에 따라 하나의 값을 선택할 때 사용한다.

---

## 23. if문 정리

- `if`문은 조건식이 true일 때만 실행된다.
- `if`문을 여러 개 쓰면 각각 독립적으로 검사된다.
- 여러 `if`문은 여러 조건이 true이면 여러 블록이 실행될 수 있다.
- 하나만 선택해야 하는 경우에는 `else if`문이 더 적합하다.
- 실행할 코드가 한 줄이면 중괄호를 생략할 수 있지만, 실수를 줄이기 위해 항상 중괄호를 쓰는 것이 좋다.

정리:

```text
if 여러 개
→ 독립 조건
→ 각각 검사
→ 여러 개 실행 가능
```

---

## 24. else if문 정리

- `else if`문은 앞 조건이 false일 때만 다음 조건을 검사한다.
- 여러 조건 중 하나만 실행된다.
- 앞에서 true가 되는 조건을 만나면 나머지는 검사하지 않는다.
- 구간 분류에 적합하다.

정리:

```text
else if
→ 연결 조건
→ 앞 조건이 false일 때 다음 조건 검사
→ 하나만 실행
```

---

## 25. switch문 정리

- `switch`문은 하나의 값을 기준으로 여러 경우를 나눌 때 사용한다.
- `case`는 비교할 값을 의미한다.
- `break`는 `switch`문을 종료한다.
- `default`는 일치하는 `case`가 없을 때 실행된다.
- `break`가 없으면 아래 `case` 코드까지 이어서 실행될 수 있다.

정리:

```text
switch 값
→ case 값과 비교
→ 일치하는 case 실행
→ break를 만나면 종료
→ 일치하는 case가 없으면 default 실행
```

---

## 26. 삼항 연산자 정리

- 삼항 연산자는 조건에 따라 하나의 값을 선택할 때 사용한다.
- 구조는 `조건식 ? 참일 때 값 : 거짓일 때 값`이다.
- 단순한 값 선택에는 유용하다.
- 조건이 복잡하거나 실행 코드가 많으면 `if-else문`을 사용하는 것이 좋다.

정리:

```text
조건식 ? true일 때 값 : false일 때 값
```

---

## 27. 오늘 새로 알게 된 점

- `switch`문은 하나의 값을 기준으로 여러 경우를 나눌 때 사용한다.
- `case`는 `switch` 값과 비교할 값을 나타낸다.
- 일치하는 `case`를 찾으면 해당 코드가 실행된다.
- `break`를 만나면 `switch`문이 종료된다.
- `break`가 없으면 아래 코드까지 계속 실행될 수 있다.
- `default`는 일치하는 `case`가 없을 때 실행된다.
- 삼항 연산자는 조건에 따라 값을 선택할 때 사용한다.
- `if`문 여러 개는 독립 조건이라 여러 결과가 나올 수 있다.
- `else if`문은 여러 조건 중 하나만 선택할 때 적합하다.
- 범위 조건은 `if문`이 적합하고, 정해진 값 비교는 `switch문`이 적합하다.

---

## 28. 헷갈린 부분

- `switch`문에서 `break`가 없으면 왜 아래 코드까지 실행되는지 헷갈릴 수 있다.
- `default`가 `else`와 비슷한 역할을 한다는 점을 기억해야 한다.
- `if문`은 범위 비교가 가능하지만, `switch문`은 값의 일치 여부를 기준으로 한다는 점을 구분해야 한다.
- 삼항 연산자는 편하지만, 복잡한 조건에서는 오히려 읽기 어려울 수 있다.
- `if`문 여러 개와 `else if`문의 차이를 계속 구분해야 한다.
- 문제 풀이에서는 조건이 여러 개 동시에 실행되어야 하는지, 하나만 선택되어야 하는지를 먼저 판단해야 한다.

---

## 29. 내 프로젝트와 연결한 부분

- 패션 추천 시스템에서 메뉴 선택 기능은 `switch`문으로 구현할 수 있다.
- 예를 들어 1번은 코디 점수 계산, 2번은 색상 분석, 3번은 핏 분석처럼 나눌 수 있다.
- 점수 구간처럼 범위를 비교할 때는 `if-else if`문이 더 적합하다.
- 단순히 추천 여부 문자열을 선택할 때는 삼항 연산자를 사용할 수 있다.

예시:

```java
int menu = 2;

switch (menu) {
    case 1:
        System.out.println("코디 점수 계산");
        break;
    case 2:
        System.out.println("색상 분석");
        break;
    case 3:
        System.out.println("핏 분석");
        break;
    default:
        System.out.println("잘못된 메뉴 선택");
}
```

---

## 30. 패션 추천 시스템 삼항 연산자 예시

```java
int totalScore = 82;

String result = totalScore >= 70 ? "추천 가능" : "보완 필요";

System.out.println(result);
```

실행 결과:

```text
추천 가능
```

---

## 31. 오늘의 핵심 정리

- 조건문은 조건에 따라 실행 흐름을 나눈다.
- `if문`은 조건식이 true일 때 실행된다.
- `else if문`은 여러 조건 중 하나만 선택할 때 사용한다.
- `switch문`은 하나의 값이 여러 값 중 무엇과 일치하는지 비교할 때 사용한다.
- `case`는 비교할 값을 나타낸다.
- `break`는 `switch`문을 종료한다.
- `default`는 일치하는 `case`가 없을 때 실행된다.
- `break`가 없으면 아래 코드까지 이어서 실행될 수 있다.
- 삼항 연산자는 조건에 따라 하나의 값을 선택할 때 사용한다.
- 범위 조건은 `if문`이 적합하다.
- 정해진 값 중 하나를 선택하는 조건은 `switch문`이 적합하다.
- 단순한 값 선택은 삼항 연산자를 사용할 수 있다.
- 조건문 단원은 프로그램의 실행 흐름을 제어하는 기본 문법이다.

---

## 32. 다음에 할 일

- 조건문 문제 다시 풀어보기
- 반복문 공부 시작하기
- `while문`과 `for문` 차이 이해하기
- 패션 추천 시스템에서 메뉴 선택 기능을 `switch문`으로 구현해보기
- 패션 추천 시스템에서 점수 결과를 삼항 연산자로 출력해보기