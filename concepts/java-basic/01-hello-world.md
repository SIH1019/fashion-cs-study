# Java Hello World 정리

## 1. 학습 범위

- Java 개발 환경
- JDK 개념
- 첫 Java 프로그램 실행
- `HelloJava` 코드 구조
- `main()` 메서드
- `System.out.println()`
- 세미콜론
- 블록
- 주석

---

## 2. 개발 환경

- Java 프로그램을 개발할 때는 IDE를 사용한다.
- 대표적인 Java IDE
  - IntelliJ IDEA
  - Eclipse

- 최근에는 IntelliJ IDEA를 많이 사용한다.
- Java 입문 단계에서는 IntelliJ IDEA Community Edition 무료 버전으로 충분하다.

---

## 3. JDK

- JDK는 Java Development Kit의 약자이다.
- Java 개발에 필요한 도구와 Java 실행 환경이 포함되어 있다.
- Java 프로그램을 만들고 실행하려면 JDK가 필요하다.

- 강의 기준
  - JDK 17 이상 사용
  - JDK 21 사용 가능
  - Oracle OpenJDK 21이 없으면 Eclipse Temurin 21을 선택해도 됨

---

## 4. 첫 Java 코드

```java
public class HelloJava {
    public static void main(String[] args) {
        System.out.println("hello java");
    }
}
```

---

## 5. 실행 결과

```text
hello java
```

---

## 6. 코드 구조 분석

### 6-1. 클래스

```java
public class HelloJava {
}
```

- `HelloJava`는 클래스 이름이다.
- Java 파일 이름과 클래스 이름은 같아야 한다.
- 예시
  - 파일명: `HelloJava.java`
  - 클래스명: `HelloJava`

- 지금 단계에서는 클래스를 자세히 이해하지 않아도 된다.
- 우선 Java 프로그램을 담는 기본 단위라고 이해한다.

---

### 6-2. main 메서드

```java
public static void main(String[] args) {
}
```

- `main()` 메서드는 Java 프로그램의 시작점이다.
- Java는 프로그램을 실행할 때 `main()` 메서드를 먼저 찾는다.
- 지금 단계에서는 `main()`을 프로그램이 시작되는 위치라고 이해한다.

---

### 6-3. 출력문

```java
System.out.println("hello java");
```

- `System.out.println()`은 값을 콘솔에 출력하는 기능이다.
- `"hello java"`는 출력할 문자열이다.
- Java에서 문자열은 큰따옴표 `"`로 감싸야 한다.

---

## 7. 세미콜론

```java
System.out.println("hello java");
```

- Java는 문장이 끝날 때 세미콜론 `;`을 붙인다.
- 세미콜론은 문장의 끝을 의미한다.
- 세미콜론을 빼면 컴파일 오류가 발생할 수 있다.

---

## 8. Java 실행 흐름

```java
public class HelloJava {
    public static void main(String[] args) {
        System.out.println("hello java");
    }
}
```

- 1단계: `HelloJava` 프로그램을 실행한다.
- 2단계: Java가 `main()` 메서드를 찾는다.
- 3단계: `System.out.println("hello java");`를 실행한다.
- 4단계: 콘솔에 `hello java`가 출력된다.
- 5단계: `main()` 메서드의 블록이 끝나면 프로그램이 종료된다.

---

## 9. 블록

```java
public class HelloJava { 
    public static void main(String[] args) { 
        System.out.println("hello java");
    } 
}
```

- `{}`는 블록을 의미한다.
- 블록은 코드의 시작과 끝을 구분한다.
- 클래스도 블록을 가진다.
- 메서드도 블록을 가진다.
- 블록 안에 있는 코드는 해당 범위 안에서 실행된다.

---

## 10. 들여쓰기

```java
public class HelloJava {
    public static void main(String[] args) {
        System.out.println("hello java");
    }
}
```

- 들여쓰기는 코드의 구조를 보기 쉽게 만든다.
- 블록이 중첩될수록 들여쓰기 깊이가 늘어난다.
- 들여쓰기를 하지 않아도 프로그램은 실행될 수 있다.
- 하지만 코드를 읽기 어려워지므로 들여쓰기를 하는 것이 좋다.
- 보통 스페이스 4칸을 사용한다.
- IntelliJ에서는 `Tab` 키를 누르면 자동으로 들여쓰기가 적용된다.

---

## 11. 여러 줄 출력

```java
public class HelloJava2 {
    public static void main(String[] args) {
        System.out.println("hello java1");
        System.out.println("hello java2");
        System.out.println("hello java3");
    }
}
```

실행 결과:

```text
hello java1
hello java2
hello java3
```

- Java 프로그램은 `main()`을 시작으로 위에서 아래로 한 줄씩 실행된다.
- 출력문을 여러 줄 작성하면 작성한 순서대로 출력된다.

---

## 12. 주석

- 주석은 코드에 설명을 적기 위해 사용한다.
- Java는 주석으로 작성된 부분을 실행하지 않는다.
- 사람이 코드를 이해하기 쉽게 만들거나, 특정 코드를 잠시 실행하지 않게 할 때 사용한다.

---

### 12-1. 한 줄 주석

```java
// 이 부분은 한 줄 주석이다.
```

- `//` 뒤에 오는 내용은 주석으로 처리된다.
- Java가 실행하지 않는다.

예시:

```java
public class CommentJava {
    public static void main(String[] args) {
        System.out.println("hello java1"); // hello java1 출력
        // System.out.println("hello java2");
    }
}
```

---

### 12-2. 여러 줄 주석

```java
/*
여러 줄 주석이다.
이 안에 있는 내용은 Java가 실행하지 않는다.
*/
```

예시:

```java
public class CommentJava {
    public static void main(String[] args) {
        System.out.println("hello java1");

        /*
        System.out.println("hello java2");
        System.out.println("hello java3");
        */
    }
}
```

---

## 13. Java 코드 작성 시 주의할 점

- Java는 대소문자를 구분한다.
- 파일명과 클래스 이름은 같아야 한다.
- 문자열은 큰따옴표 `"`로 감싸야 한다.
- 문장이 끝나면 세미콜론 `;`을 붙여야 한다.
- `{}` 블록의 시작과 끝을 잘 맞춰야 한다.
- 들여쓰기를 하면 코드 구조를 이해하기 쉽다.
- 주석은 Java가 실행하지 않는다.

---

## 14. 오늘 배운 핵심 정리

- Java 프로그램은 `main()` 메서드에서 시작한다.
- `System.out.println()`은 콘솔에 값을 출력하는 기능이다.
- 문자열은 큰따옴표로 감싼다.
- Java는 대소문자를 구분한다.
- 세미콜론은 문장의 끝을 의미한다.
- `{}`는 코드의 범위를 나타내는 블록이다.
- 주석은 Java가 읽지 않고 무시하는 설명 부분이다.

---

## 15. 내 프로젝트와 연결하기

패션 추천 시스템에서도 기본 출력 구조가 필요하다.

예시:

```java
public class FashionStart {
    public static void main(String[] args) {
        System.out.println("패션 추천 시스템 시작");
        System.out.println("사용자가 입력한 코디를 분석합니다.");
    }
}
```

- `main()` 메서드에서 프로그램이 시작된다.
- `System.out.println()`을 사용해 분석 결과를 출력할 수 있다.
- 앞으로 변수와 조건문을 배우면 사용자가 입력한 옷 정보에 따라 다른 결과를 출력할 수 있다.

---

## 16. 다음에 공부할 내용

- 변수
- 변수 선언
- 변수 초기화
- 변수 값 변경
- 변수 타입