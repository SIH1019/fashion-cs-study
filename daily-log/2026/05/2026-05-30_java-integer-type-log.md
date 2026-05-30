# 2026-05-30 Java 변수 타입 학습 개발일지

## 1. 오늘 공부한 주제

- Java 변수 타입
- 정수 타입
- 실수 타입
- 불린형
- 문자 타입
- 문자열 타입
- 자주 사용하는 타입
- 변수 명명 규칙 전까지 학습

---

## 2. 오늘 공부한 범위

- `변수 타입1`
- `변수 타입2`
- 자주 사용하는 타입
- 변수 명명 규칙 전까지

---

## 3. 오늘 공부하지 않은 범위

- 변수 명명 규칙
- 문제와 풀이
- 변수 단원 최종 정리

---

## 4. 변수 타입이 필요한 이유

- 변수는 값을 저장하는 공간이다.
- 변수에 아무 값이나 저장할 수 있는 것은 아니다.
- 저장하려는 값의 종류에 따라 타입을 정해야 한다.
- 정수, 실수, 참/거짓, 문자, 문자열은 각각 사용하는 타입이 다르다.
- Java는 변수의 타입에 맞는 값만 저장할 수 있다.

---

## 5. 변수 타입 예시

```java
int a = 100;
double b = 10.5;
boolean c = true;
char d = 'A';
String e = "Hello Java";
```

정리:

```text
int     → 정수
double  → 실수
boolean → true / false
char    → 문자 하나
String  → 문자열
```

---

## 6. int

```java
int a = 100;
```

- 정수를 저장하는 타입이다.
- 소수점이 없는 숫자를 저장할 때 사용한다.
- Java에서 가장 기본적으로 많이 사용하는 정수 타입이다.
- 점수, 나이, 개수 같은 값에 사용할 수 있다.

예시:

```java
int age = 22;
int score = 85;
int colorScore = 82;
```

---

## 7. double

```java
double b = 10.5;
```

- 실수를 저장하는 타입이다.
- 소수점이 있는 숫자를 저장할 때 사용한다.
- 키, 몸무게, 평균값, 비율 같은 값을 저장할 때 사용할 수 있다.
- 실수 타입은 보통 `double`을 사용하면 된다.

예시:

```java
double height = 166.5;
double averageScore = 82.7;
```

---

## 8. boolean

```java
boolean c = true;
```

- 참과 거짓을 저장하는 타입이다.
- 저장할 수 있는 값은 `true`, `false` 두 가지이다.
- 조건문에서 자주 사용된다.
- 어떤 상태가 맞는지 아닌지 판단할 때 사용할 수 있다.

예시:

```java
boolean isStudent = true;
boolean isMatched = false;
```

---

## 9. char

```java
char d = 'A';
```

- 문자 하나를 저장하는 타입이다.
- 작은따옴표 `' '`를 사용한다.
- 문자 하나만 저장할 수 있다.

예시:

```java
char grade = 'A';
char size = 'M';
```

주의:

```java
char grade = 'A';
```

- 가능

```java
char grade = "A";
```

- 불가능
- `char`는 작은따옴표를 사용해야 한다.

---

## 10. String

```java
String e = "Hello Java";
```

- 문자열을 저장하는 타입이다.
- 큰따옴표 `" "`를 사용한다.
- 문자 하나뿐 아니라 여러 글자를 저장할 수 있다.
- 이름, 색상, 설명, 문장 같은 값을 저장할 때 사용한다.
- `String`은 첫 글자가 대문자로 시작하는 특별한 타입이다.

예시:

```java
String name = "Inhye";
String topColor = "navy";
String comment = "어두운 색 조합입니다.";
```

---

## 11. 타입에 맞는 값 사용

- Java에서는 변수 타입에 맞는 값을 넣어야 한다.
- 타입과 값이 맞지 않으면 컴파일 오류가 발생한다.

예시:

```java
int a = 100;
double b = 10.5;
boolean c = true;
char d = 'A';
String e = "Hello Java";
```

- `int`에는 정수
- `double`에는 실수
- `boolean`에는 `true` 또는 `false`
- `char`에는 문자 하나
- `String`에는 문자열

---

## 12. 정수 타입

- 정수 타입은 소수점이 없는 숫자를 저장할 때 사용한다.
- Java의 정수 타입은 다음과 같다.

```text
byte
short
int
long
```

---

## 13. byte

```java
byte b = 127;
```

- 정수를 저장하는 타입이다.
- 크기는 `1byte`이다.
- 저장 범위는 `-128 ~ 127`이다.
- 저장할 수 있는 범위가 작다.
- 일반적인 계산에서는 자주 사용하지 않는다.

정리:

```text
byte
크기: 1byte
범위: -128 ~ 127
```

---

## 14. short

```java
short s = 32767;
```

- 정수를 저장하는 타입이다.
- 크기는 `2byte`이다.
- 저장 범위는 `-32,768 ~ 32,767`이다.
- `byte`보다 큰 숫자를 저장할 수 있다.
- 일반적인 계산에서는 자주 사용하지 않는다.

정리:

```text
short
크기: 2byte
범위: -32,768 ~ 32,767
```

---

## 15. int

```java
int i = 2147483647;
```

- 정수를 저장할 때 가장 많이 사용하는 타입이다.
- 크기는 `4byte`이다.
- 저장 범위는 `-2,147,483,648 ~ 2,147,483,647`이다.
- 일반적인 정수 계산은 대부분 `int`를 사용한다.

정리:

```text
int
크기: 4byte
범위: -2,147,483,648 ~ 2,147,483,647
```

---

## 16. long

```java
long l = 9223372036854775807L;
```

- 아주 큰 정수를 저장할 때 사용하는 타입이다.
- 크기는 `8byte`이다.
- `int`보다 훨씬 큰 숫자를 저장할 수 있다.
- 큰 금액, 조회수, 전체 데이터 수처럼 숫자가 매우 커질 수 있는 경우에 사용한다.

정리:

```text
long
크기: 8byte
범위: -9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807
```

---

## 17. long 타입에서 L을 붙이는 이유

```java
long bigNumber = 3000000000L;
```

- Java에서 정수 숫자는 기본적으로 `int`로 인식된다.
- `3000000000`은 `int` 범위를 넘어간다.
- 그래서 Java에게 이 숫자가 `long` 타입이라는 것을 알려줘야 한다.
- 이때 숫자 뒤에 `L`을 붙인다.
- 소문자 `l`도 가능하지만 숫자 `1`과 헷갈릴 수 있다.
- 그래서 대문자 `L`을 사용하는 것이 좋다.

---

## 18. 실수 타입

- 실수 타입은 소수점이 있는 숫자를 저장할 때 사용한다.
- Java의 실수 타입은 다음과 같다.

```text
float
double
```

---

## 19. float

```java
float f = 10.5f;
```

- 실수를 저장하는 타입이다.
- 크기는 `4byte`이다.
- 숫자 뒤에 `f`를 붙여야 한다.
- Java에서 실수 숫자는 기본적으로 `double`로 인식되기 때문이다.
- 일반적인 실수 계산에서는 잘 사용하지 않는다.

정리:

```text
float
크기: 4byte
특징: 숫자 뒤에 f 필요
```

---

## 20. double

```java
double d = 10.5;
```

- 실수를 저장하는 타입이다.
- 크기는 `8byte`이다.
- Java에서 실수는 기본적으로 `double`을 사용한다.
- 소수점이 있는 값은 대부분 `double`로 처리하면 된다.

정리:

```text
double
크기: 8byte
특징: 일반적인 실수 계산에 사용
```

---

## 21. 자주 사용하는 타입

- 정수
  - `int`
  - `long`

- 실수
  - `double`

- 참 / 거짓
  - `boolean`

- 문자열
  - `String`

정리:

```text
정수       → int, long
실수       → double
참/거짓    → boolean
문자열     → String
```

---

## 22. 실무에서 타입을 고르는 기준

- 일반적인 정수는 `int`를 사용한다.
- 20억이 넘을 것 같은 큰 정수는 `long`을 사용한다.
- 파일을 바이트 단위로 다룰 때는 `byte`를 사용할 수 있다.
- 실수는 고민하지 말고 `double`을 사용하면 된다.
- 참과 거짓은 `boolean`을 사용한다.
- 문자는 문자 하나든 문자열이든 대부분 `String`을 사용하는 것이 편하다.

---

## 23. 오늘 작성한 예제 코드

```java
package variable;

public class VarTypePractice {
    public static void main(String[] args) {
        int age = 22;
        double height = 166.5;
        boolean isStudent = true;
        char grade = 'A';
        String name = "Inhye";

        int colorScore = 82;
        long totalAnalysisCount = 3000000000L;

        System.out.println(age);
        System.out.println(height);
        System.out.println(isStudent);
        System.out.println(grade);
        System.out.println(name);
        System.out.println(colorScore);
        System.out.println(totalAnalysisCount);
    }
}
```

실행 결과:

```text
22
166.5
true
A
Inhye
82
3000000000
```

---

## 24. 오늘 새로 알게 된 점

- 변수 타입은 변수에 저장할 값의 종류를 정하는 기준이다.
- `int`는 정수를 저장한다.
- `double`은 실수를 저장한다.
- `boolean`은 `true`, `false`만 저장한다.
- `char`는 문자 하나를 저장한다.
- `String`은 문자열을 저장한다.
- 정수 타입에는 `byte`, `short`, `int`, `long`이 있다.
- 실수 타입에는 `float`, `double`이 있다.
- 일반적인 정수는 `int`를 사용한다.
- 아주 큰 정수는 `long`을 사용한다.
- 일반적인 실수는 `double`을 사용한다.
- `long` 값에는 필요할 때 `L`을 붙인다.
- `float` 값에는 `f`를 붙인다.

---

## 25. 헷갈린 부분

- 타입이 왜 여러 개인지 헷갈렸다.
- `int`와 `long`을 언제 나눠 써야 하는지 헷갈렸다.
- `float`와 `double`의 차이가 헷갈렸다.
- `long`에는 왜 `L`을 붙이는지 헷갈렸다.
- `float`에는 왜 `f`를 붙이는지 헷갈렸다.
- `char`는 작은따옴표를 쓰고, `String`은 큰따옴표를 쓴다는 점이 헷갈릴 수 있다고 느꼈다.

---

## 26. 내 프로젝트와 연결한 부분

- 패션 추천 시스템에서 옷 정보와 점수를 저장할 때 변수 타입이 필요하다.
- 색상, 핏, 상황 설명은 `String`으로 저장할 수 있다.
- 색상 점수, 핏 점수, 전체 점수는 `int`로 저장할 수 있다.
- 키나 비율처럼 소수점이 필요한 값은 `double`로 저장할 수 있다.
- 추천 가능 여부나 조건 만족 여부는 `boolean`으로 저장할 수 있다.
- 전체 분석 횟수처럼 매우 큰 숫자는 `long`으로 저장할 수 있다.

예시:

```java
String topColor = "navy";
String bottomColor = "black";

int colorScore = 82;
int fitScore = 78;
int totalScore = colorScore + fitScore;

double heightRatio = 1.2;

boolean isColorMatched = true;

long totalAnalysisCount = 3000000000L;
```

정리:

```text
topColor            → 상의 색상
bottomColor         → 하의 색상
colorScore          → 색상 점수
fitScore            → 핏 점수
totalScore          → 전체 점수
heightRatio         → 비율
isColorMatched      → 색상 조합 적합 여부
totalAnalysisCount  → 전체 분석 횟수
```

---

## 27. 오늘의 핵심 정리

- 변수 타입은 저장할 값의 종류를 정한다.
- Java에서는 타입에 맞는 값만 변수에 저장할 수 있다.
- 정수는 `int`를 기본으로 사용한다.
- 큰 정수는 `long`을 사용한다.
- 실수는 `double`을 기본으로 사용한다.
- 참과 거짓은 `boolean`을 사용한다.
- 문자 하나는 `char`를 사용할 수 있다.
- 문자열은 `String`을 사용한다.
- 실무에서는 `int`, `long`, `double`, `boolean`, `String`을 자주 사용한다.
- 오늘은 변수 명명 규칙 전까지 공부했다.

---

## 28. 다음에 할 일

- 변수 명명 규칙 공부하기
- 변수 이름에 사용할 수 있는 문자 정리하기
- 변수 이름에 사용할 수 없는 경우 정리하기
- Java 예약어 공부하기
- 카멜 케이스 공부하기
- 패션 추천 시스템에서 사용할 변수명 정리하기