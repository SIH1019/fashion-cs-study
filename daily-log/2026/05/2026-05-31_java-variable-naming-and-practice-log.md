# 2026-05-31 Java 변수 명명 규칙 및 문제 풀이 개발일지

## 1. 오늘 공부한 주제

- Java 변수 명명 규칙
- 변수 이름 작성 관례
- 패키지 이름 작성 관례
- 클래스 이름 작성 관례
- 메서드 이름 작성 관례
- 카멜 케이스
- 변수 문제 풀이
- 변수 값을 이용한 연산
- 연산 결과를 새로운 변수에 저장하는 방식

---

## 2. 오늘 공부한 범위

- 변수 명명 규칙
- Java 이름 작성 관례
- 문제와 풀이

---

## 3. 오늘 공부하지 않은 범위

- 조건문
- 반복문
- 메서드
- 객체지향
- 변수 타입 전체 재정리

---

## 4. 변수 명명 규칙이 필요한 이유

- 변수 이름은 마음대로 지을 수 있지만, Java 문법상 지켜야 하는 규칙이 있다.
- 규칙을 지키지 않으면 컴파일 오류가 발생한다.
- 변수 이름은 단순히 짧게 짓는 것보다 의미가 잘 보이게 짓는 것이 중요하다.
- 변수 이름만 보고 어떤 값을 저장하는지 알 수 있어야 한다.
- 코드가 길어질수록 변수 이름이 명확해야 헷갈리지 않는다.

---

## 5. 변수 이름에 사용할 수 있는 문자

- 영문자
- 숫자
- 달러 기호 `$`
- 밑줄 `_`

예시:

```java
int age;
int userAge;
int user_age;
int $money;
int num1;
```

- 위 변수 이름들은 사용할 수 있다.
- 숫자는 변수 이름에 포함할 수 있다.
- 하지만 숫자로 시작할 수는 없다.
- `$`와 `_`도 사용할 수 있지만, 일반적인 Java 변수명에서는 자주 사용하지 않는 것이 좋다.

---

## 6. 변수 이름에 사용할 수 없는 경우

### 6-1. 숫자로 시작할 수 없음

잘못된 예시:

```java
int 1num;
int 1st;
```

- 변수 이름은 숫자로 시작할 수 없다.
- 숫자를 변수 이름 중간이나 끝에 넣는 것은 가능하다.

가능한 예시:

```java
int num1;
int myVar1;
```

---

### 6-2. 공백을 사용할 수 없음

잘못된 예시:

```java
int user age;
int color score;
```

- 변수 이름에는 공백을 넣을 수 없다.
- 여러 단어를 사용할 때는 카멜 케이스를 사용한다.

가능한 예시:

```java
int userAge;
int colorScore;
```

---

### 6-3. Java 예약어를 사용할 수 없음

잘못된 예시:

```java
int int;
int class;
int public;
```

- `int`, `class`, `public`은 Java에서 이미 정해진 의미로 사용되는 단어이다.
- 이런 단어를 예약어라고 한다.
- 예약어는 변수 이름으로 사용할 수 없다.

---

## 7. Java 이름 작성 관례

- Java에서는 변수 이름뿐만 아니라 패키지, 클래스, 메서드 이름에도 작성 관례가 있다.
- 문법 규칙을 지키는 것도 중요하지만, 관례를 지키면 코드 구조를 더 쉽게 이해할 수 있다.
- 이름만 봐도 이것이 패키지인지, 클래스인지, 변수인지, 메서드인지 구분할 수 있어야 한다.
- 관례를 지키면 나중에 코드가 길어져도 읽기 쉽다.

---

### 7-1. 패키지 이름 작성 관례

```java
package variable.ex;
```

- 패키지 이름은 모두 소문자로 작성한다.
- 패키지는 Java 파일을 분류하는 폴더 역할을 한다.
- 여러 단어가 필요하면 보통 `.`으로 구분한다.
- 패키지 이름은 대문자로 시작하지 않는다.

좋은 예시:

```java
package variable;
package variable.ex;
package javastudy.variable;
package fashion.score;
```

좋지 않은 예시:

```java
package Variable;
package VariableEx;
package JavaStudy.Variable;
package Fashion.Score;
```

정리:

```text
패키지 이름 → 모두 소문자
```

---

### 7-2. 클래스 이름 작성 관례

```java
public class VarEx1 {
}
```

- 클래스 이름은 대문자로 시작한다.
- 여러 단어를 사용할 때는 각 단어의 첫 글자를 대문자로 쓴다.
- 이것을 파스칼 케이스라고 한다.

좋은 예시:

```java
HelloJava
VarEx1
FashionScorePractice
```

좋지 않은 예시:

```java
helloJava
varex1
fashionScorePractice
```

정리:

```text
클래스 이름 → 대문자로 시작
여러 단어 → 각 단어 첫 글자 대문자
```

---

### 7-3. 변수 이름 작성 관례

- 변수 이름은 소문자로 시작하는 것이 일반적이다.
- 여러 단어를 연결할 때는 카멜 케이스를 사용한다.
- 변수 이름은 값의 의미가 드러나도록 작성하는 것이 좋다.
- 너무 짧고 의미 없는 이름은 피하는 것이 좋다.

좋지 않은 예시:

```java
int a;
int b;
int x;
```

- 어떤 값을 의미하는지 알기 어렵다.
- 코드가 길어지면 해석하기 힘들다.

좋은 예시:

```java
int age;
int score;
int colorScore;
String topColor;
boolean isColorMatched;
```

- 변수 이름만 봐도 어떤 값을 저장하는지 알 수 있다.
- 나중에 코드를 다시 봐도 이해하기 쉽다.

정리:

```text
변수 이름 → 소문자로 시작
여러 단어 → 카멜 케이스 사용
```

---

### 7-4. 메서드 이름 작성 관례

```java
printScore();
calculateTotalScore();
```

- 메서드 이름은 변수 이름처럼 소문자로 시작한다.
- 여러 단어를 사용할 때는 카멜 케이스를 사용한다.
- 메서드는 보통 동작을 나타내기 때문에 동사로 시작하는 경우가 많다.

좋은 예시:

```java
printScore();
calculateTotalScore();
checkColorMatch();
```

좋지 않은 예시:

```java
PrintScore();
calculate_total_score();
CheckColorMatch();
```

정리:

```text
메서드 이름 → 소문자로 시작
여러 단어 → 카멜 케이스 사용
```

---

### 7-5. Java 이름 작성 관례 전체 정리

```text
패키지 이름 → 모두 소문자
클래스 이름 → 대문자로 시작
변수 이름 → 소문자로 시작, 카멜 케이스
메서드 이름 → 소문자로 시작, 카멜 케이스
```

예시:

```java
package fashion.score;

public class FashionScorePractice {
    public static void main(String[] args) {
        int colorScore = 82;
        int fitScore = 78;
        int totalScore = colorScore + fitScore;

        System.out.println(totalScore);
    }
}
```

- `fashion.score`
  - 패키지 이름
  - 모두 소문자

- `FashionScorePractice`
  - 클래스 이름
  - 대문자로 시작
  - 여러 단어의 첫 글자를 대문자로 작성

- `main`
  - 메서드 이름
  - 소문자로 시작

- `colorScore`, `fitScore`, `totalScore`
  - 변수 이름
  - 소문자로 시작
  - 카멜 케이스 사용

- `println`
  - 메서드 이름
  - 소문자로 시작

---

## 8. 카멜 케이스

- 카멜 케이스는 여러 단어를 이어서 변수 이름이나 메서드 이름을 만들 때 사용하는 방식이다.
- 첫 번째 단어는 소문자로 시작한다.
- 두 번째 단어부터는 첫 글자를 대문자로 쓴다.
- Java 변수 이름과 메서드 이름에서는 카멜 케이스를 자주 사용한다.

예시:

```java
int userAge;
int colorScore;
int totalScore;
String topColor;
String bottomColor;
boolean isColorMatched;
```

정리:

```text
user age          → 불가능
user_age          → 가능하지만 Java 변수명에서는 보통 덜 사용
userAge           → Java에서 자주 쓰는 방식

color score       → 불가능
color_score       → 가능하지만 Java 변수명에서는 보통 덜 사용
colorScore        → Java에서 자주 쓰는 방식

is color matched  → 불가능
isColorMatched    → Java에서 자주 쓰는 방식
```

---

## 9. 변수 명명 규칙 핵심 정리

- 변수 이름은 영문자, 숫자, `$`, `_`를 사용할 수 있다.
- 변수 이름은 숫자로 시작할 수 없다.
- 변수 이름에는 공백을 사용할 수 없다.
- Java 예약어는 변수 이름으로 사용할 수 없다.
- 변수 이름은 소문자로 시작하는 것이 일반적이다.
- 여러 단어를 연결할 때는 카멜 케이스를 사용한다.
- 변수 이름은 짧은 것보다 의미가 잘 드러나는 것이 중요하다.
- 변수 이름만 보고 어떤 값을 저장하는지 알 수 있어야 한다.

---

## 10. 문제 풀이 1

### 10-1. 문제 내용

- 변수 `num1`에 숫자 값을 저장한다.
- 변수 `num2`에 숫자 값을 저장한다.
- 두 변수의 덧셈 결과를 출력한다.
- 두 변수의 뺄셈 결과를 출력한다.
- 두 변수의 곱셈 결과를 출력한다.

---

### 10-2. 작성 코드

```java
package variable.ex;

public class VarEx1 {
    public static void main(String[] args) {
        int num1 = 4;
        int num2 = 3;

        System.out.println(num1 + num2);
        System.out.println(num1 - num2);
        System.out.println(num1 * num2);
    }
}
```

---

### 10-3. 실행 결과

```text
7
1
12
```

---

### 10-4. 풀이 정리

- `num1`에는 `4`를 저장했다.
- `num2`에는 `3`을 저장했다.
- `num1 + num2`는 `4 + 3`이므로 결과는 `7`이다.
- `num1 - num2`는 `4 - 3`이므로 결과는 `1`이다.
- `num1 * num2`는 `4 * 3`이므로 결과는 `12`이다.
- 변수에 저장된 값을 이용해서 계산할 수 있다는 것을 확인했다.

---

## 11. 문제 풀이 2

### 11-1. 문제 내용

- 클래스 이름은 `VarEx2`로 작성한다.
- 변수 `num1`을 선언하고 `10`을 할당한다.
- 변수 `num2`를 선언하고 `20`을 할당한다.
- 두 변수의 합을 구한다.
- 결과를 새로운 변수 `sum`에 저장한다.
- `sum` 변수의 값을 출력한다.

---

### 11-2. 작성 코드

```java
package variable.ex;

public class VarEx2 {
    public static void main(String[] args) {
        int num1 = 10;
        int num2 = 20;
        int sum = num1 + num2;

        System.out.println(sum);
    }
}
```

---

### 11-3. 실행 결과

```text
30
```

---

### 11-4. 풀이 정리

- `num1`에는 `10`을 저장했다.
- `num2`에는 `20`을 저장했다.
- `num1 + num2`는 `10 + 20`이다.
- 계산 결과는 `30`이다.
- 이 결과를 `sum` 변수에 저장했다.
- `System.out.println(sum);`을 실행하면 `sum`에 저장된 `30`이 출력된다.

실행 흐름:

```text
1. int num1 = 10;           → num1에 10 저장
2. int num2 = 20;           → num2에 20 저장
3. int sum = num1 + num2;   → 10 + 20 계산 후 sum에 30 저장
4. System.out.println(sum); → sum 값 30 출력
```

---

## 12. 문제 풀이를 통해 이해한 점

- 변수에는 값을 저장할 수 있다.
- 변수에 저장된 값은 계산에 사용할 수 있다.
- 계산 결과를 바로 출력할 수도 있다.
- 계산 결과를 새로운 변수에 저장할 수도 있다.
- 새로운 변수에 저장하면 나중에 같은 결과를 다시 사용할 수 있다.
- 변수 이름을 의미 있게 지으면 코드의 역할을 이해하기 쉽다.

---

## 13. 오늘 새로 알게 된 점

- 변수 이름에는 문법 규칙과 관례가 있다.
- 문법 규칙을 지키지 않으면 컴파일 오류가 발생한다.
- 패키지 이름은 모두 소문자로 작성한다.
- 클래스 이름은 대문자로 시작한다.
- 메서드 이름도 변수 이름처럼 소문자로 시작하고 카멜 케이스를 사용한다.
- 변수 이름은 숫자로 시작할 수 없다.
- 변수 이름에는 공백을 사용할 수 없다.
- Java 예약어는 변수 이름으로 사용할 수 없다.
- Java 변수 이름은 보통 카멜 케이스를 사용한다.
- 변수 이름은 의미 있게 짓는 것이 좋다.
- 변수에 저장된 값을 이용해서 덧셈, 뺄셈, 곱셈을 할 수 있다.
- 계산 결과를 새로운 변수에 저장할 수 있다.

---

## 14. 헷갈린 부분

- 변수 이름에 숫자를 넣을 수는 있지만 숫자로 시작할 수는 없다는 점
- `_`를 사용할 수는 있지만 Java에서는 보통 카멜 케이스를 더 자주 쓴다는 점
- 예약어와 일반 변수 이름을 구분해야 한다는 점
- 패키지 이름은 소문자로 작성하고, 클래스 이름은 대문자로 시작한다는 점
- 변수 이름과 메서드 이름은 둘 다 소문자로 시작하고 카멜 케이스를 사용한다는 점
- 계산 결과를 바로 출력하는 것과 변수에 저장한 뒤 출력하는 것의 차이
- 변수 이름을 짧게 짓는 것보다 의미 있게 짓는 것이 더 중요하다는 점

---

## 15. 내 프로젝트와 연결한 부분

- 패션 추천 시스템에서도 변수 이름을 의미 있게 지어야 한다.
- 패션 추천 시스템의 패키지 이름은 모두 소문자로 작성하는 것이 좋다.
- 패션 추천 시스템의 클래스 이름은 대문자로 시작하고 역할이 드러나게 작성하는 것이 좋다.
- 색상, 핏, 기장, 점수, 판단 결과를 변수 이름만 보고 알 수 있어야 한다.
- 변수 이름이 명확해야 이후 조건문과 알고리즘을 만들 때 헷갈리지 않는다.
- 계산 결과를 새로운 변수에 저장하는 방식은 패션 점수 계산에도 그대로 사용할 수 있다.

예시:

```java
String topColor = "navy";
String bottomColor = "black";

int colorScore = 82;
int fitScore = 78;
int totalScore = colorScore + fitScore;

boolean isColorMatched = true;
```

정리:

```text
topColor       → 상의 색상
bottomColor    → 하의 색상
colorScore     → 색상 점수
fitScore       → 핏 점수
totalScore     → 전체 점수
isColorMatched → 색상 조합 적합 여부
```

---

## 16. 패션 추천 시스템에 적용할 수 있는 예시 코드

```java
package fashion.score;

public class FashionScorePractice {
    public static void main(String[] args) {
        String topColor = "navy";
        String bottomColor = "black";

        int colorScore = 82;
        int fitScore = 78;
        int totalScore = colorScore + fitScore;

        boolean isColorMatched = true;

        System.out.println(topColor);
        System.out.println(bottomColor);
        System.out.println(colorScore);
        System.out.println(fitScore);
        System.out.println(totalScore);
        System.out.println(isColorMatched);
    }
}
```

실행 결과:

```text
navy
black
82
78
160
true
```

---

## 17. 오늘의 핵심 정리

- 변수 이름은 규칙에 맞게 작성해야 한다.
- 변수 이름은 숫자로 시작할 수 없다.
- 변수 이름에는 공백을 사용할 수 없다.
- Java 예약어는 변수 이름으로 사용할 수 없다.
- 변수 이름에는 영문자, 숫자, `$`, `_`를 사용할 수 있다.
- 패키지 이름은 모두 소문자로 작성한다.
- 클래스 이름은 대문자로 시작한다.
- 변수 이름은 소문자로 시작하고 카멜 케이스를 사용한다.
- 메서드 이름도 소문자로 시작하고 카멜 케이스를 사용한다.
- 변수 이름은 의미 있게 지어야 한다.
- 변수에 저장된 값은 연산에 사용할 수 있다.
- 연산 결과는 바로 출력할 수도 있고, 새로운 변수에 저장할 수도 있다.
- 계산 결과를 변수에 저장하면 이후 코드에서 재사용하기 쉽다.

---

## 18. 다음에 할 일

- 변수 단원 최종 정리하기
- 변수 문제 다시 풀어보기
- 변수 타입과 변수 이름을 함께 사용해서 간단한 예제 만들기
- 조건문 `if` 공부 시작하기
- 패션 추천 시스템에서 사용할 변수명 목록 정리하기