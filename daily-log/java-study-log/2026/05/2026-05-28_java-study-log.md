# 2026-05-28 Java 학습 개발일지

## 1. 오늘의 목표

- Java 입문 강의 전체 흐름 확인
- Hello World 코드 구조 복습
- 변수 개념 학습
- 변수 선언과 초기화 이해
- 변수 값 변경 방식 이해
- 초기화하지 않은 변수 사용 시 발생하는 오류 이해
- 학습 내용을 GitHub에 정리

---

## 2. 오늘 공부한 자료

- `0. 목차.pdf`
- `1. Hello World.pdf`
- `2. 변수.pdf`

---

## 3. 오늘 공부한 범위

- Java 입문 전체 목차 확인
- Hello World 파트 정리
- 변수 파트 8페이지까지 학습

---

## 4. 오늘 정리한 파일

- `concepts/java-basic/00-outline.md`
- `concepts/java-basic/01-hello-world.md`
- `concepts/java-basic/02-variable.md`

---

## 5. Java 입문 목차 확인

- Java 입문 강의의 전체 흐름을 확인함
- 학습 순서
  - Hello World
  - 변수
  - 연산자
  - 조건문
  - 반복문
  - 스코프, 형변환
  - 배열
  - 메서드
  - 다음으로

- 현재 진행 상황
  - Hello World 파트 정리
  - 변수 파트 8페이지까지 학습

---

## 6. Hello World 파트 학습 내용

### 6-1. 개발 환경

- Java 개발에는 IntelliJ IDEA 또는 Eclipse 같은 IDE를 사용할 수 있음
- 최근에는 IntelliJ IDEA를 많이 사용함
- Java 입문 단계에서는 IntelliJ IDEA Community Edition 무료 버전으로 충분함
- Java 프로그램을 개발하고 실행하려면 JDK가 필요함

---

### 6-2. 첫 Java 코드

```java
public class HelloJava {
    public static void main(String[] args) {
        System.out.println("hello java");
    }
}
```

---

### 6-3. 실행 결과

```text
hello java
```

---

### 6-4. 코드 구조

- `public class HelloJava`
  - `HelloJava`는 클래스 이름
  - Java 파일 이름과 클래스 이름은 같아야 함
  - 예시
    - 파일명: `HelloJava.java`
    - 클래스명: `HelloJava`

- `public static void main(String[] args)`
  - Java 프로그램의 시작점
  - Java는 `main()` 메서드를 찾아서 프로그램을 실행함

- `System.out.println("hello java");`
  - 콘솔에 값을 출력하는 코드
  - 문자열은 큰따옴표 `"`로 감싸야 함
  - 문장이 끝나면 세미콜론 `;`을 붙여야 함

---

### 6-5. Hello World에서 배운 핵심

- Java 프로그램은 `main()` 메서드에서 시작함
- `System.out.println()`은 콘솔 출력 기능임
- Java는 대소문자를 구분함
- 문자열은 큰따옴표로 감싸야 함
- 문장이 끝나면 세미콜론을 붙여야 함
- `{}`는 코드의 범위를 나타내는 블록임
- 주석은 Java가 실행하지 않는 설명 부분임

---

## 7. 변수 파트 학습 내용

### 7-1. 변수의 필요성

- 같은 값을 여러 번 직접 쓰면 수정이 어려움
- 예를 들어 `10`을 여러 번 출력하는 코드에서 `20`으로 바꾸려면 모든 위치를 수정해야 함
- 변수를 사용하면 값을 한 곳에 저장하고 여러 번 재사용할 수 있음
- 변수는 데이터를 담는 저장 공간으로 이해할 수 있음

---

### 7-2. 변수 선언

```java
int a;
```

- `int`는 정수를 저장하는 타입
- `a`는 변수 이름
- `int a;`는 정수를 저장할 수 있는 변수 `a`를 만드는 코드
- 변수를 만드는 것을 변수 선언이라고 함

---

### 7-3. 변수 초기화

```java
a = 10;
```

- 선언한 변수에 처음으로 값을 저장하는 것을 변수 초기화라고 함
- Java에서 `=`는 오른쪽 값을 왼쪽 변수에 저장한다는 뜻
- 수학에서 말하는 “같다”와는 의미가 다름

---

### 7-4. 변수 값 읽기

```java
System.out.println(a);
```

- 변수 이름을 쓰면 변수에 저장된 값을 읽을 수 있음
- `a`에 `10`이 저장되어 있으면 `System.out.println(a);`는 `10`을 출력함
- 변수 값을 읽어도 값이 사라지지는 않음
- 같은 변수는 여러 번 사용할 수 있음

---

### 7-5. 변수 값 변경

```java
int a;
a = 10;
System.out.println(a);

a = 50;
System.out.println(a);
```

실행 결과:

```text
10
50
```

- 변수는 값을 변경할 수 있음
- `a = 10;` 이후에는 변수 `a`에 `10`이 저장됨
- `a = 50;`을 실행하면 기존 값 `10`은 사라지고 `50`으로 변경됨
- 이후 `a`를 출력하면 `50`이 출력됨

---

### 7-6. 변수 선언과 초기화 방법

- 선언과 초기화를 따로 할 수 있음

```java
int a;
a = 1;
```

- 선언과 초기화를 한 번에 할 수 있음

```java
int b = 2;
```

- 여러 변수를 한 번에 선언하고 초기화할 수 있음

```java
int c = 3, d = 4;
```

---

### 7-7. 초기화하지 않은 변수 사용 오류

```java
int a;
System.out.println(a);
```

- 위 코드는 오류가 발생함
- 이유는 변수 `a`가 초기화되지 않았기 때문임

오류 예시:

```text
java: variable a might not have been initialized
```

- Java는 초기화하지 않은 지역 변수를 사용할 수 없게 막음
- 변수를 사용하기 전에는 반드시 값을 넣어야 함

---

## 8. 오늘 작성한 예시 코드

```java
public class FashionVariablePractice {
    public static void main(String[] args) {
        String topColor = "navy";
        String bottomColor = "black";
        String shoesColor = "white";

        int colorScore = 82;
        int fitScore = 78;
        int totalScore = colorScore + fitScore;

        System.out.println("상의 색상: " + topColor);
        System.out.println("하의 색상: " + bottomColor);
        System.out.println("신발 색상: " + shoesColor);

        System.out.println("색상 점수: " + colorScore);
        System.out.println("핏 점수: " + fitScore);
        System.out.println("총점: " + totalScore);
    }
}
```

---

## 9. 프로젝트와 연결한 부분

- 패션 추천 시스템에서도 변수는 기본적으로 필요함
- 사용자가 입력한 옷 정보를 변수에 저장할 수 있음
- 색상, 핏, 기장, 상황 정보를 변수로 관리할 수 있음
- 색상 점수, 핏 점수, 전체 점수도 변수로 저장할 수 있음
- 앞으로 조건문을 배우면 변수 값에 따라 다른 분석 결과를 출력할 수 있음

예시:

```java
String topColor = "navy";
String bottomColor = "black";
String shoesColor = "white";

int colorScore = 82;
int fitScore = 78;
int totalScore = colorScore + fitScore;
```

- `topColor`
  - 상의 색상을 저장하는 변수

- `bottomColor`
  - 하의 색상을 저장하는 변수

- `shoesColor`
  - 신발 색상을 저장하는 변수

- `colorScore`
  - 색상 조합 점수를 저장하는 변수

- `fitScore`
  - 핏 점수를 저장하는 변수

- `totalScore`
  - 전체 코디 점수를 저장하는 변수

---

## 10. 오늘 헷갈린 부분

- 변수 선언과 초기화의 차이
- `=`가 수학의 같다와 다르다는 점
- 변수 값을 변경하면 기존 값이 사라진다는 점
- 초기화하지 않은 변수를 사용할 수 없는 이유
- 변수에 저장된 값을 읽어도 값이 사라지지 않는다는 점
- Java 파일 이름과 클래스 이름을 같게 맞춰야 한다는 점
- 세미콜론을 빠뜨리면 오류가 날 수 있다는 점

---

## 11. 오늘의 핵심 정리

- Java 프로그램은 `main()` 메서드에서 시작함
- `System.out.println()`은 콘솔에 값을 출력하는 기능임
- 변수는 값을 저장하는 공간임
- 변수는 같은 값을 여러 번 사용할 때 유용함
- `int a;`는 변수 선언임
- `a = 10;`은 변수에 값을 저장하는 코드임
- 변수를 처음으로 값과 연결하는 것을 초기화라고 함
- 변수 값은 나중에 변경할 수 있음
- 초기화하지 않은 변수는 사용할 수 없음
- 패션 추천 시스템에서도 옷 정보와 점수를 저장하기 위해 변수가 필요함

---

## 12. 다음에 할 일

- 변수 타입 공부
- `int`, `double`, `boolean`, `char`, `String` 정리
- 변수 이름 짓는 규칙 공부
- 조건문 `if` 공부
- 패션 추천 시스템에서 색상 조합을 조건문으로 판단하는 코드 작성