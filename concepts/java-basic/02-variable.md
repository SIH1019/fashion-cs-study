# Java 변수 정리

## 1. 학습 범위

- 변수의 필요성
- 패키지
- 변수 선언
- 변수에 값 대입
- 변수 초기화
- 변수 값 읽기
- 변수 값 변경
- 여러 변수 선언
- 선언과 초기화 방식
- 초기화하지 않은 변수 사용 오류
- 프로젝트 적용 예시

---

## 2. 패키지

```java
package variable;
```

- 패키지는 Java 파일을 구분하기 위한 폴더처럼 이해하면 된다.
- `variable`이라는 패키지를 만들었다면 Java 파일 첫 줄에 `package variable;`을 적어야 한다.
- Java 파일이 위치한 패키지와 코드에 적은 패키지 선언이 같아야 한다.

예시:

```java
package variable;

public class Var1 {
    public static void main(String[] args) {
        System.out.println(10);
    }
}
```

---

## 3. 변수의 필요성

### 3-1. 변수를 사용하지 않는 경우

```java
package variable;

public class Var1 {
    public static void main(String[] args) {
        System.out.println(10);
        System.out.println(10);
        System.out.println(10);
    }
}
```

실행 결과:

```text
10
10
10
```

- 숫자 `10`을 3번 직접 출력하는 코드이다.
- 만약 `10`을 `20`으로 바꾸려면 코드 3곳을 모두 수정해야 한다.
- 만약 같은 값이 100곳에 있다면 100곳을 모두 수정해야 한다.
- 이런 문제를 해결하기 위해 변수를 사용한다.

---

### 3-2. 변수를 사용하는 경우

```java
package variable;

public class Var2 {
    public static void main(String[] args) {
        int a;
        a = 10;

        System.out.println(a);
        System.out.println(a);
        System.out.println(a);
    }
}
```

실행 결과:

```text
10
10
10
```

- 변수 `a`에 `10`을 저장했다.
- 이후 `a`를 여러 번 출력했다.
- 값을 바꾸고 싶으면 `a`에 저장하는 값만 바꾸면 된다.

---

## 4. 변수란?

- 변수는 값을 저장할 수 있는 공간이다.
- 쉽게 말하면 데이터를 담는 그릇이다.
- 변수는 이름 그대로 값이 변할 수 있다.
- 값을 여러 번 재사용할 때 유용하다.
- 값이 바뀌어도 변수에 저장된 값만 변경하면 되므로 코드 관리가 쉬워진다.

---

## 5. 변수 선언

```java
int a;
```

- `int`는 정수를 저장할 수 있는 타입이다.
- `a`는 변수 이름이다.
- `int a;`는 정수를 저장할 수 있는 `a`라는 저장 공간을 만드는 코드이다.
- 이렇게 변수를 만드는 것을 변수 선언이라고 한다.

정리:

```text
int a;
```

- `int`: 저장할 값의 종류
- `a`: 변수 이름
- `;`: 문장 끝

---

## 6. 변수에 값 대입

```java
a = 10;
```

- Java에서 `=`는 오른쪽 값을 왼쪽 변수에 저장한다는 뜻이다.
- 수학에서 말하는 “같다”와는 의미가 다르다.
- `a = 10;`은 변수 `a`에 숫자 `10`을 저장한다는 뜻이다.

정리:

```text
a = 10;
```

- 오른쪽 값: `10`
- 왼쪽 저장 공간: `a`
- 의미: `10`을 `a`에 저장

---

## 7. 변수 초기화

```java
int a;
a = 10;
```

- 변수를 선언한 뒤 처음으로 값을 저장하는 것을 변수 초기화라고 한다.
- 위 코드에서는 `a = 10;`이 변수 초기화이다.
- 변수를 사용하기 전에는 반드시 초기화해야 한다.

---

## 8. 변수 값 읽기

```java
System.out.println(a);
```

- 변수에 저장된 값을 사용하려면 변수 이름을 적으면 된다.
- `a`에 `10`이 저장되어 있으면 Java는 실행 시점에 `a`의 값을 읽어서 사용한다.

실행 흐름:

```java
System.out.println(a);
System.out.println(10);
```

- 변수 값을 읽는다고 해서 값이 사라지는 것은 아니다.
- 같은 변수는 여러 번 읽을 수 있다.

---

## 9. 변수 값 변경

```java
package variable;

public class Var3 {
    public static void main(String[] args) {
        int a;

        a = 10;
        System.out.println(a);

        a = 50;
        System.out.println(a);
    }
}
```

실행 결과:

```text
10
50
```

- 변수는 값을 변경할 수 있다.
- 처음에는 `a`에 `10`이 저장된다.
- `a = 50;`이 실행되면 기존 값 `10`은 사라지고 `50`으로 바뀐다.
- 이후 `a`를 출력하면 `50`이 출력된다.

실행 순서:

```text
1. int a;        → 정수를 저장할 변수 a 생성
2. a = 10;       → a에 10 저장
3. println(a);   → a의 값 10 출력
4. a = 50;       → a의 값을 50으로 변경
5. println(a);   → a의 값 50 출력
```

---

## 10. 변수 선언 방식

### 10-1. 하나씩 선언하기

```java
int a;
int b;
```

- 변수는 하나씩 선언할 수 있다.

---

### 10-2. 여러 개를 한 번에 선언하기

```java
int c, d;
```

- 같은 타입의 변수는 한 번에 여러 개 선언할 수 있다.

---

## 11. 변수 선언과 초기화 방식

### 11-1. 선언과 초기화를 따로 하기

```java
int a;
a = 1;
System.out.println(a);
```

- 먼저 변수 `a`를 선언한다.
- 이후 `a`에 값 `1`을 저장한다.

---

### 11-2. 선언과 초기화를 한 번에 하기

```java
int b = 2;
System.out.println(b);
```

- 변수 `b`를 선언하면서 동시에 `2`를 저장한다.
- 실무에서는 이 방식이 자주 사용된다.

---

### 11-3. 여러 변수를 한 번에 선언하고 초기화하기

```java
int c = 3, d = 4;
System.out.println(c);
System.out.println(d);
```

- 변수 `c`와 `d`를 한 번에 선언했다.
- 각각 `3`, `4`로 초기화했다.

---

## 12. 변수는 초기화해야 한다

초기화하지 않은 변수를 사용하면 컴파일 에러가 발생한다.

```java
package variable;

public class Var6 {
    public static void main(String[] args) {
        int a;
        System.out.println(a);
    }
}
```

오류 예시:

```text
java: variable a might not have been initialized
```

- 변수 `a`를 선언만 하고 값을 넣지 않았기 때문에 오류가 발생한다.
- Java는 초기화하지 않은 지역 변수를 사용할 수 없게 막는다.
- 초기화하지 않은 변수에는 어떤 값이 들어있는지 알 수 없다.
- 따라서 변수를 사용하기 전에는 반드시 값을 넣어야 한다.

---

## 13. 컴파일 에러

- 컴파일 에러는 Java 문법에 맞지 않을 때 발생한다.
- 초기화하지 않은 변수를 사용하는 것도 컴파일 에러이다.
- 컴파일 에러는 프로그램 실행 전에 문제를 알려준다.
- 오류를 빨리 찾을 수 있기 때문에 좋은 에러라고 볼 수 있다.

---

## 14. 오늘 배운 핵심 정리

- 변수는 값을 저장하는 공간이다.
- 변수는 데이터를 담는 그릇처럼 이해할 수 있다.
- `int a;`는 정수를 저장할 변수 `a`를 선언하는 코드이다.
- `a = 10;`은 변수 `a`에 값 `10`을 저장하는 코드이다.
- 변수를 처음으로 값과 연결하는 것을 초기화라고 한다.
- 변수에 저장된 값은 여러 번 읽을 수 있다.
- 변수 값을 읽어도 값이 사라지지 않는다.
- 변수 값은 나중에 변경할 수 있다.
- 변수 값이 변경되면 기존 값은 사라진다.
- 초기화하지 않은 변수는 사용할 수 없다.

---

## 15. 내 프로젝트와 연결하기

패션 추천 시스템에서도 변수는 가장 기본적으로 필요하다.

사용자가 입력한 옷 정보와 분석 점수를 변수에 저장할 수 있다.

예시:

```java
String topColor = "navy";
String bottomColor = "black";
String shoesColor = "white";

int colorScore = 82;
int fitScore = 78;
int totalScore = colorScore + fitScore;
```

- `topColor`: 상의 색상
- `bottomColor`: 하의 색상
- `shoesColor`: 신발 색상
- `colorScore`: 색상 점수
- `fitScore`: 핏 점수
- `totalScore`: 전체 점수

---

## 16. 프로젝트 적용 예시 코드

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

실행 결과 예시:

```text
상의 색상: navy
하의 색상: black
신발 색상: white
색상 점수: 82
핏 점수: 78
총점: 160
```

---

## 17. 앞으로 확장할 방향

- 지금은 변수에 값을 직접 저장했다.
- 이후 조건문을 배우면 변수 값에 따라 다른 판단을 할 수 있다.

예시:

```java
if (topColor.equals("black") && bottomColor.equals("black")) {
    System.out.println("전체적으로 어두운 조합입니다.");
}
```

- 패션 추천 시스템에서는 이런 방식으로 색상, 핏, 기장, 상황을 판단할 수 있다.
- 변수는 앞으로 알고리즘을 만들기 위한 기본 재료가 된다.

---

## 18. 다음에 공부할 내용

- 변수 타입
- `int`
- `double`
- `boolean`
- `char`
- `String`
- 변수 이름 짓는 규칙
- 조건문 `if`
- 색상 조합에 따라 점수를 다르게 주는 코드 작성