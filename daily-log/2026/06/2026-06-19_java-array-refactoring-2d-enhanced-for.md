# 2026-06-19 Java 배열 리팩토링, 2차원 배열, 향상된 for문 정리

## 1. 오늘 공부한 내용

오늘은 Java 입문 강의의 `배열` 단원에서 다음 내용을 공부했다.

- 배열 리팩토링
- 배열의 길이 `length`
- 배열과 for문
- 배열의 총합과 평균 구하기
- 2차원 배열
- 2차원 배열의 행과 열
- `arr.length`
- `arr[row].length`
- 2차원 배열 리팩토링
- 2차원 배열에 값을 자동으로 넣기
- 2차원 배열 출력하기
- 향상된 for문
- 향상된 for문을 사용할 수 없는 경우

이번 범위에서 중요한 것은 배열을 만들고 끝나는 것이 아니라,
배열에 들어있는 값을 반복문으로 더 편하게 처리하는 방법을 익히는 것이었다.

특히 내가 헷갈렸던 부분은 다음이었다.

```text
1. total = 0이 무슨 뜻인지
2. students.length가 배열 길이가 맞는지
3. 2차원 배열에서 중첩 for문이 왜 두 번 나오는지
4. 두 중첩 for문이 똑같이 생겼는데 뭐가 다른지
5. 향상된 for문은 일반 for문과 뭐가 다른지
```

---

## 2. 배열 리팩토링이란?

리팩토링은 프로그램의 실행 결과는 그대로 유지하면서,
코드 구조를 더 좋게 바꾸는 것이다.

배열을 사용하기 전에는 학생 점수를 각각 다른 변수로 관리했다.

```java
int student1 = 90;
int student2 = 80;
int student3 = 70;
int student4 = 60;
int student5 = 50;
```

이렇게 하면 학생이 많아질수록 변수를 계속 만들어야 한다.

출력할 때도 다음처럼 하나씩 써야 한다.

```java
System.out.println("학생1 점수: " + student1);
System.out.println("학생2 점수: " + student2);
System.out.println("학생3 점수: " + student3);
System.out.println("학생4 점수: " + student4);
System.out.println("학생5 점수: " + student5);
```

배열을 사용하면 같은 타입의 값을 하나로 묶을 수 있다.

```java
int[] students = {90, 80, 70, 60, 50};
```

이렇게 하면 학생 점수 5개를 `students`라는 배열 하나로 관리할 수 있다.

---

## 3. 배열과 인덱스

배열의 각 칸은 인덱스로 접근한다.

```java
int[] students = {90, 80, 70, 60, 50};
```

이 배열은 다음과 같이 이해할 수 있다.

```text
students[0] = 90
students[1] = 80
students[2] = 70
students[3] = 60
students[4] = 50
```

배열은 1번부터 시작하지 않고 0번부터 시작한다.

따라서 배열에 값이 5개 있어도 인덱스는 다음과 같다.

```text
0, 1, 2, 3, 4
```

마지막 인덱스는 5가 아니라 4이다.

---

## 4. students.length

`students.length`는 배열의 길이를 의미한다.

```java
int[] students = {90, 80, 70, 60, 50};
```

이 배열에는 값이 5개 있다.

그래서 다음 값은 5이다.

```java
students.length
```

정리하면 다음과 같다.

```text
students.length
→ students 배열의 길이
→ 배열 안에 값이 몇 개 있는지 알려줌
→ 여기서는 5
```

주의할 점은 `students.length`가 마지막 인덱스가 아니라는 것이다.

```text
students.length = 5
마지막 인덱스 = 4
```

배열은 0부터 시작하기 때문에 마지막 인덱스는 항상 `배열 길이 - 1`이다.

---

## 5. 배열과 for문

배열의 값을 하나씩 출력하려면 다음처럼 직접 쓸 수도 있다.

```java
System.out.println(students[0]);
System.out.println(students[1]);
System.out.println(students[2]);
System.out.println(students[3]);
System.out.println(students[4]);
```

하지만 배열의 값이 많아지면 코드가 길어진다.

그래서 배열은 보통 for문과 함께 사용한다.

```java
for (int i = 0; i < students.length; i++) {
    System.out.println(students[i]);
}
```

여기서 `i`는 배열의 인덱스 역할을 한다.

```text
i = 0 → students[0]
i = 1 → students[1]
i = 2 → students[2]
i = 3 → students[3]
i = 4 → students[4]
```

조건식은 다음과 같다.

```java
i < students.length
```

`students.length`가 5이므로 실제로는 다음과 같다.

```java
i < 5
```

그래서 `i`는 0, 1, 2, 3, 4까지만 반복한다.

---

## 6. 왜 i <= students.length가 아니라 i < students.length인가?

배열 길이가 5이면 사용할 수 있는 인덱스는 0부터 4까지이다.

```text
students.length = 5
사용 가능한 인덱스 = 0, 1, 2, 3, 4
```

만약 조건을 이렇게 쓰면 안 된다.

```java
i <= students.length
```

이렇게 쓰면 `i`가 5일 때도 반복문이 실행된다.

그러면 다음 코드가 실행될 수 있다.

```java
students[5]
```

하지만 `students[5]`는 존재하지 않는다.

그래서 배열을 반복할 때는 보통 다음처럼 쓴다.

```java
for (int i = 0; i < students.length; i++)
```

이렇게 하면 마지막 인덱스인 4까지만 접근하므로 안전하다.

---

## 7. 배열의 총합과 평균 구하기

내가 작성한 코드는 다음과 같다.

```java
package array.ex;

public class ArrayEx1 {

    public static void main(String[] args) {
        int students[] = {90, 80, 70, 60, 50};

        int total = 0;
        for (int i = 0; i < students.length; i++) {
            total += students[i];
        }

        double average = (double) total / students.length;

        System.out.println("점수 총합: " + total);
        System.out.println("점수 평균: " + average);
    }
}
```

이 코드는 학생 점수 배열의 총합과 평균을 구하는 코드이다.

---

## 8. total = 0의 의미

```java
int total = 0;
```

`total`은 점수들을 하나씩 더해서 누적할 변수이다.

내가 이해한 것처럼 `total = 0`은 빈 바구니라고 생각하면 된다.

처음에는 아무 점수도 더하지 않았기 때문에 0부터 시작한다.

```text
total
→ 점수들을 담을 빈 바구니
→ 아직 아무 점수도 더하지 않았기 때문에 0
```

이후 반복문이 돌면서 점수를 하나씩 더한다.

```java
total += students[i];
```

이 코드는 다음과 같은 의미이다.

```java
total = total + students[i];
```

즉, 기존 `total`에 현재 학생 점수를 더해서 다시 `total`에 저장한다.

---

## 9. total 값이 변하는 과정

배열은 다음과 같다.

```java
int[] students = {90, 80, 70, 60, 50};
```

처음 상태는 다음과 같다.

```text
total = 0
```

반복문이 돌면서 다음처럼 값이 변한다.

```text
i = 0
students[0] = 90
total = 0 + 90
total = 90

i = 1
students[1] = 80
total = 90 + 80
total = 170

i = 2
students[2] = 70
total = 170 + 70
total = 240

i = 3
students[3] = 60
total = 240 + 60
total = 300

i = 4
students[4] = 50
total = 300 + 50
total = 350
```

반복문이 끝나면 최종 총합은 다음과 같다.

```text
total = 350
```

---

## 10. 평균 구하기

평균을 구하는 코드는 다음과 같다.

```java
double average = (double) total / students.length;
```

여기서 `students.length`는 배열 길이이다.

```text
students.length = 5
```

따라서 계산은 다음과 같다.

```text
average = 350 / 5
average = 70.0
```

`(double) total`을 사용하는 이유는 평균은 소수점이 나올 수 있기 때문이다.

예를 들어 총합이 351이고 학생 수가 5명이면 평균은 다음과 같다.

```text
351 / 5 = 70.2
```

그런데 `int / int`로 계산하면 소수점이 버려질 수 있다.

그래서 `total`을 먼저 `double`로 바꿔서 실수 계산이 되도록 한다.

```java
(double) total / students.length
```

---

## 11. 2차원 배열

지금까지 사용한 배열은 1차원 배열이다.

```java
int[] students = {90, 80, 70, 60, 50};
```

1차원 배열은 한 줄로 값을 저장하는 구조이다.

```text
[0] [1] [2] [3] [4]
90  80  70  60  50
```

2차원 배열은 행과 열을 가진 배열이다.

```java
int[][] arr = new int[2][3];
```

이 코드는 2행 3열짜리 배열을 만든다.

그림으로 보면 다음과 같다.

```text
[0][0] [0][1] [0][2]
[1][0] [1][1] [1][2]
```

처음 값은 `int`의 기본값인 0이다.

```text
0 0 0
0 0 0
```

---

## 12. 2차원 배열에서 행과 열

2차원 배열은 행과 열로 접근한다.

```java
arr[row][column]
```

여기서:

```text
row
→ 행

column
→ 열
```

예를 들어 다음과 같다.

```text
arr[0][0] → 0행 0열
arr[0][1] → 0행 1열
arr[0][2] → 0행 2열

arr[1][0] → 1행 0열
arr[1][1] → 1행 1열
arr[1][2] → 1행 2열
```

---

## 13. 2차원 배열 초기화

2차원 배열은 다음처럼 초기화할 수 있다.

```java
int[][] arr = {
    {1, 2, 3},
    {4, 5, 6}
};
```

이렇게 쓰면 행과 열이 더 잘 보인다.

```text
1 2 3
4 5 6
```

바깥 중괄호는 전체 2차원 배열이고,
안쪽 중괄호는 각 행이다.

```text
{1, 2, 3}
→ 0행

{4, 5, 6}
→ 1행
```

---

## 14. 2차원 배열에서 arr.length

2차원 배열에서 `arr.length`는 행의 개수를 의미한다.

```java
int[][] arr = {
    {1, 2, 3},
    {4, 5, 6}
};
```

여기서 행은 2개이다.

```text
{1, 2, 3}
{4, 5, 6}
```

그래서 다음 값은 2이다.

```java
arr.length
```

정리하면 다음과 같다.

```text
arr.length
→ 행의 길이
→ 여기서는 2
```

---

## 15. 2차원 배열에서 arr[row].length

`arr[row].length`는 현재 행의 열 개수를 의미한다.

```java
int[][] arr = {
    {1, 2, 3},
    {4, 5, 6}
};
```

여기서 `arr[0]`은 다음 배열이다.

```java
{1, 2, 3}
```

이 배열에는 값이 3개 있다.

그래서:

```java
arr[0].length
```

의 값은 3이다.

`arr[1]`도 다음 배열이다.

```java
{4, 5, 6}
```

이 배열에도 값이 3개 있다.

그래서:

```java
arr[1].length
```

의 값도 3이다.

정리하면 다음과 같다.

```text
arr.length
→ 행의 개수

arr[row].length
→ 현재 row 행의 열 개수
```

---

## 16. 2차원 배열 출력 코드

2차원 배열을 출력하는 코드는 다음과 같다.

```java
package array;

public class ArrayDi3 {
    public static void main(String[] args) {
        int[][] arr = {
            {1, 2, 3},
            {4, 5, 6}
        };

        for (int row = 0; row < arr.length; row++) {
            for (int column = 0; column < arr[row].length; column++) {
                System.out.print(arr[row][column] + " ");
            }
            System.out.println();
        }
    }
}
```

여기서 바깥 for문은 행을 담당한다.

```java
for (int row = 0; row < arr.length; row++)
```

안쪽 for문은 열을 담당한다.

```java
for (int column = 0; column < arr[row].length; column++)
```

출력 부분은 다음이다.

```java
System.out.print(arr[row][column] + " ");
```

한 행의 출력이 끝나면 줄바꿈을 해야 하므로 다음 코드를 사용한다.

```java
System.out.println();
```

출력 결과는 다음과 같다.

```text
1 2 3
4 5 6
```

---

## 17. 2차원 배열 출력 흐름

2행 3열 배열은 다음 순서로 출력된다.

```text
row = 0, column = 0 → arr[0][0] 출력 → 1
row = 0, column = 1 → arr[0][1] 출력 → 2
row = 0, column = 2 → arr[0][2] 출력 → 3
row = 0 한 행이 끝남 → 줄바꿈

row = 1, column = 0 → arr[1][0] 출력 → 4
row = 1, column = 1 → arr[1][1] 출력 → 5
row = 1, column = 2 → arr[1][2] 출력 → 6
row = 1 한 행이 끝남 → 줄바꿈
```

그래서 출력 결과가 다음처럼 나온다.

```text
1 2 3
4 5 6
```

---

## 18. 2차원 배열 리팩토링 - 값 입력

파일의 `ArrayDi4`에서는 배열에 직접 값을 하나하나 넣지 않고,
배열의 크기와 상관없이 순서대로 1씩 증가하는 값을 입력하도록 개선한다.

코드는 다음과 같다.

```java
package array;

public class ArrayDi4 {
    public static void main(String[] args) {
        int[][] arr = new int[2][3];

        int i = 1;

        for (int row = 0; row < arr.length; row++) {
            for (int column = 0; column < arr[row].length; column++) {
                arr[row][column] = i++;
            }
        }

        for (int row = 0; row < arr.length; row++) {
            for (int column = 0; column < arr[row].length; column++) {
                System.out.print(arr[row][column] + " ");
            }
            System.out.println();
        }
    }
}
```

이 코드에는 중첩 for문이 두 번 나온다.

첫 번째 중첩 for문은 값을 넣는 코드이고,
두 번째 중첩 for문은 값을 출력하는 코드이다.

---

## 19. 첫 번째 중첩 for문: 배열에 값 넣기

첫 번째 중첩 for문은 다음이다.

```java
int i = 1;

for (int row = 0; row < arr.length; row++) {
    for (int column = 0; column < arr[row].length; column++) {
        arr[row][column] = i++;
    }
}
```

이 반복문은 배열에 값을 넣는 역할을 한다.

핵심 코드는 다음이다.

```java
arr[row][column] = i++;
```

이 코드는 현재 배열 칸에 `i` 값을 넣고,
그 다음 `i`를 1 증가시킨다.

처음에는 `i = 1`이다.

실행 흐름은 다음과 같다.

```text
arr[0][0] = 1
arr[0][1] = 2
arr[0][2] = 3
arr[1][0] = 4
arr[1][1] = 5
arr[1][2] = 6
```

이 반복문이 끝나면 배열 상태는 다음과 같다.

```text
1 2 3
4 5 6
```

이때는 아직 화면에 출력된 것이 아니다.

배열 안에 값만 저장된 상태이다.

---

## 20. i++의 의미

```java
arr[row][column] = i++;
```

여기서 `i++`는 후위 증가 연산자이다.

즉, 먼저 현재 `i` 값을 사용하고,
그 다음 `i`를 1 증가시킨다.

처음 `i = 1`이면 다음처럼 동작한다.

```text
arr[0][0] = i++;
→ arr[0][0]에 1을 넣음
→ 그 다음 i는 2가 됨
```

다음 칸에서는 `i = 2`가 사용된다.

```text
arr[0][1] = i++;
→ arr[0][1]에 2를 넣음
→ 그 다음 i는 3이 됨
```

그래서 배열에 1부터 6까지 순서대로 들어간다.

---

## 21. 두 번째 중첩 for문: 배열 출력하기

두 번째 중첩 for문은 다음이다.

```java
for (int row = 0; row < arr.length; row++) {
    for (int column = 0; column < arr[row].length; column++) {
        System.out.print(arr[row][column] + " ");
    }
    System.out.println();
}
```

이 반복문은 배열에 들어있는 값을 출력하는 역할을 한다.

핵심 코드는 다음이다.

```java
System.out.print(arr[row][column] + " ");
```

이 코드는 현재 배열 칸에 들어있는 값을 읽어서 화면에 출력한다.

출력 흐름은 다음과 같다.

```text
arr[0][0] 출력 → 1
arr[0][1] 출력 → 2
arr[0][2] 출력 → 3
줄바꿈

arr[1][0] 출력 → 4
arr[1][1] 출력 → 5
arr[1][2] 출력 → 6
줄바꿈
```

최종 출력은 다음과 같다.

```text
1 2 3
4 5 6
```

---

## 22. 왜 중첩 for문이 두 번 나올까?

두 중첩 for문은 겉모양이 거의 똑같다.

```java
for (int row = 0; row < arr.length; row++) {
    for (int column = 0; column < arr[row].length; column++) {
        ...
    }
}
```

겉모양이 같은 이유는 둘 다 2차원 배열 전체를 한 칸씩 방문해야 하기 때문이다.

하지만 안에서 하는 일이 다르다.

첫 번째 중첩 for문은 값을 넣는다.

```java
arr[row][column] = i++;
```

두 번째 중첩 for문은 값을 출력한다.

```java
System.out.print(arr[row][column] + " ");
```

정리하면 다음과 같다.

```text
첫 번째 중첩 for문
→ 저장용
→ 배열 상태를 바꿈
→ 화면에 출력하지 않음

두 번째 중첩 for문
→ 출력용
→ 배열 값을 읽음
→ 화면에 출력함
→ 배열 상태는 바꾸지 않음
```

따라서 두 반복문은 모양은 같지만 역할이 다르다.

---

## 23. 2차원 배열 크기를 바꿔도 동작하는 이유

`ArrayDi4`에서는 다음 코드로 길이를 활용한다.

```java
arr.length
arr[row].length
```

그래서 배열 크기를 바꿔도 반복문 코드를 크게 바꾸지 않아도 된다.

예를 들어:

```java
int[][] arr = new int[4][5];
```

로 바꾸면 4행 5열 배열이 된다.

그러면 `arr.length`는 4가 되고,
각 행의 `arr[row].length`는 5가 된다.

결과적으로 값이 1부터 20까지 들어가고 출력된다.

```text
1 2 3 4 5
6 7 8 9 10
11 12 13 14 15
16 17 18 19 20
```

이렇게 배열의 길이를 사용하면 배열 크기가 달라져도 반복문을 더 유연하게 사용할 수 있다.

---

## 24. 향상된 for문

향상된 for문은 배열의 값을 처음부터 끝까지 하나씩 꺼낼 때 사용하는 문법이다.

다른 말로 for-each문이라고도 한다.

기본 구조는 다음과 같다.

```java
for (변수 : 배열) {
    // 배열의 값을 하나씩 꺼내서 실행할 코드
}
```

예를 들어 다음 배열이 있다.

```java
int[] numbers = {1, 2, 3, 4, 5};
```

일반 for문으로 출력하면 다음과 같다.

```java
for (int i = 0; i < numbers.length; ++i) {
    int number = numbers[i];
    System.out.println(number);
}
```

이 코드는 배열의 인덱스 `i`를 사용해서 값을 하나씩 꺼낸다.

---

## 25. 향상된 for문 코드

같은 코드를 향상된 for문으로 쓰면 다음과 같다.

```java
for (int number : numbers) {
    System.out.println(number);
}
```

이 코드는 다음처럼 읽으면 된다.

```text
numbers 배열에서 값을 하나씩 꺼낸다.
꺼낸 값을 number 변수에 담는다.
number를 출력한다.
배열 끝까지 반복한다.
```

실행 흐름은 다음과 같다.

```text
1번째 반복:
number = 1
출력: 1

2번째 반복:
number = 2
출력: 2

3번째 반복:
number = 3
출력: 3

4번째 반복:
number = 4
출력: 4

5번째 반복:
number = 5
출력: 5
```

향상된 for문은 인덱스와 종료 조건을 직접 작성하지 않아도 된다.

그래서 배열을 처음부터 끝까지 단순히 탐색할 때 코드가 더 간단해진다.

---

## 26. 일반 for문과 향상된 for문 비교

일반 for문:

```java
for (int i = 0; i < numbers.length; ++i) {
    int number = numbers[i];
    System.out.println(number);
}
```

향상된 for문:

```java
for (int number : numbers) {
    System.out.println(number);
}
```

두 코드는 같은 결과를 출력한다.

하지만 일반 for문은 다음 내용을 직접 작성해야 한다.

```text
1. 인덱스 변수 i 선언
2. 종료 조건 i < numbers.length
3. i 증가
4. numbers[i]로 배열 값 꺼내기
```

향상된 for문은 이런 부분을 생략하고,
배열에서 값을 하나씩 꺼내준다.

정리하면 다음과 같다.

```text
일반 for문
→ 인덱스를 직접 사용함

향상된 for문
→ 인덱스를 직접 사용하지 않음
→ 배열 값을 하나씩 꺼내서 변수에 담아줌
```

---

## 27. 향상된 for문을 사용할 수 있는 경우

향상된 for문은 배열의 값을 처음부터 끝까지 순서대로 읽을 때 사용하기 좋다.

예를 들어 모든 숫자를 출력하는 경우에 사용할 수 있다.

```java
int[] numbers = {1, 2, 3, 4, 5};

for (int number : numbers) {
    System.out.println(number);
}
```

또 배열의 모든 값을 더할 때도 사용할 수 있다.

```java
int[] numbers = {1, 2, 3, 4, 5};

int total = 0;

for (int number : numbers) {
    total += number;
}

System.out.println(total);
```

이 경우 인덱스가 필요하지 않고,
배열의 값만 하나씩 꺼내면 되기 때문에 향상된 for문이 잘 맞는다.

---

## 28. 향상된 for문을 사용할 수 없는 경우

향상된 for문은 항상 사용할 수 있는 것은 아니다.

향상된 for문은 인덱스 값을 직접 사용하지 않는다.

그래서 인덱스 번호가 필요한 경우에는 일반 for문을 사용해야 한다.

파일의 예시는 다음과 같다.

```java
for (int i = 0; i < numbers.length; ++i) {
    System.out.println("number" + i + "번의 결과는: " + numbers[i]);
}
```

이 코드는 `i` 값을 출력에 사용한다.

```text
number0번의 결과는: 1
number1번의 결과는: 2
number2번의 결과는: 3
```

이렇게 인덱스 값이 필요하면 향상된 for문보다 일반 for문이 적합하다.

억지로 향상된 for문을 사용할 수도 있다.

```java
int i = 0;
for (int number : numbers) {
    System.out.println("number" + i + "번의 결과는: " + number);
    i++;
}
```

하지만 이렇게 쓸 거면 일반 for문을 사용하는 것이 더 좋다.

---

## 29. 일반 for문을 써야 하는 경우

다음과 같은 경우에는 일반 for문을 쓰는 것이 좋다.

```text
1. 인덱스 번호가 필요할 때
2. number0, number1처럼 번호를 출력해야 할 때
3. 배열의 특정 위치를 직접 다뤄야 할 때
4. 현재 위치 i를 계산에 사용해야 할 때
```

향상된 for문은 배열의 값을 하나씩 꺼내는 데 편하지만,
인덱스를 직접 사용해야 하는 문제에는 맞지 않는다.

---

## 30. 향상된 for문 핵심 정리

향상된 for문은 배열을 처음부터 끝까지 순서대로 탐색할 때 사용한다.

```java
for (int number : numbers) {
    System.out.println(number);
}
```

읽는 방법은 다음과 같다.

```text
numbers 배열에서 값을 하나씩 꺼내서
number 변수에 담고
반복문 안의 코드를 실행한다.
```

장점은 다음과 같다.

```text
1. 인덱스를 직접 만들지 않아도 된다.
2. 종료 조건을 직접 쓰지 않아도 된다.
3. 코드가 간결하다.
4. 배열 전체를 읽을 때 편하다.
```

단점은 다음과 같다.

```text
1. 인덱스를 직접 사용할 수 없다.
2. 인덱스 번호가 필요한 경우에는 불편하다.
3. 특정 위치를 기준으로 처리해야 하면 일반 for문이 더 좋다.
```

---

## 31. 오늘 헷갈렸던 부분 정리

오늘 헷갈렸던 부분은 다음이었다.

```text
total = 0은 무슨 뜻인가?
students.length는 배열 길이가 맞는가?
2차원 배열에서 중첩 for문이 왜 두 번 나오는가?
두 중첩 for문은 똑같이 생겼는데 뭐가 다른가?
향상된 for문은 일반 for문과 뭐가 다른가?
```

정리하면 다음과 같다.

```text
total = 0
→ 점수를 더하기 위한 빈 바구니이다.
→ 아직 아무 점수도 더하지 않았기 때문에 0부터 시작한다.

students.length
→ students 배열의 길이이다.
→ {90, 80, 70, 60, 50}이면 길이는 5이다.

첫 번째 중첩 for문
→ 2차원 배열에 값을 넣는 반복문이다.

두 번째 중첩 for문
→ 2차원 배열의 값을 출력하는 반복문이다.

두 중첩 for문이 비슷하게 생긴 이유
→ 둘 다 2차원 배열 전체를 방문해야 하기 때문이다.

두 중첩 for문의 차이
→ 안쪽에서 하는 일이 다르다.
→ 하나는 저장, 하나는 출력이다.

향상된 for문
→ 배열의 값을 하나씩 꺼낼 때 사용하는 for문이다.
→ 인덱스가 필요 없으면 편하다.
→ 인덱스가 필요하면 일반 for문을 써야 한다.
```

---

## 32. 내가 이해한 핵심

오늘 이해한 핵심은 배열은 반복문과 함께 사용할 때 훨씬 편해진다는 것이다.

배열은 여러 값을 하나의 이름으로 묶어준다.

반복문은 그 배열의 값을 하나씩 꺼내서 처리하게 해준다.

```java
for (int i = 0; i < students.length; i++) {
    total += students[i];
}
```

이 코드는 배열의 인덱스를 사용해서 점수를 하나씩 꺼낸다.

향상된 for문은 같은 일을 더 간단하게 할 수 있다.

```java
for (int score : students) {
    total += score;
}
```

하지만 향상된 for문은 인덱스를 직접 사용하지 않기 때문에,
인덱스가 필요한 경우에는 일반 for문을 사용해야 한다.

2차원 배열에서는 행과 열이 있으므로 중첩 for문을 사용한다.

```text
바깥 for문
→ 행 담당

안쪽 for문
→ 열 담당
```

그리고 2차원 배열 전체를 돌면서 값을 넣을 때도 중첩 for문,
전체를 돌면서 값을 출력할 때도 중첩 for문을 사용한다.

모양은 같지만 역할은 다르다.

```text
저장용 중첩 for문
출력용 중첩 for문
```

---

## 33. 내가 만들려는 프로젝트와의 연결

내가 만들고 싶은 프로젝트는 패션 추천 시스템이다.

이 시스템은 색상, 핏, 기장, 상황 등을 분석해서 옷 조합을 추천하고 설명하는 방향이다.

배열과 반복문은 나중에 여러 개의 옷 정보나 추천 점수를 다룰 때 사용할 수 있다.

예를 들어 옷 이름을 배열에 저장할 수 있다.

```java
String[] clothes = {"네이비 셔츠", "블랙 슬랙스", "화이트 스니커즈"};
```

향상된 for문을 사용하면 옷 목록을 간단히 출력할 수 있다.

```java
for (String item : clothes) {
    System.out.println(item);
}
```

추천 점수도 배열로 관리할 수 있다.

```java
int[] scores = {85, 70, 90};

int total = 0;
for (int score : scores) {
    total += score;
}

double average = (double) total / scores.length;
```

이 코드는 다음처럼 연결될 수 있다.

```text
scores[0] → 색상 조합 점수
scores[1] → 핏 점수
scores[2] → 상황 적합도 점수
```

2차원 배열은 여러 코디 후보와 여러 평가 기준을 관리할 때 사용할 수 있다.

```text
          색상  핏  상황
코디1      80  70  90
코디2      90  60  85
```

이 구조는 2차원 배열로 표현할 수 있다.

```java
int[][] outfitScores = {
    {80, 70, 90},
    {90, 60, 85}
};
```

나중에는 이 배열을 반복문으로 돌면서 각 코디의 평균 점수를 계산하고,
가장 높은 점수의 코디를 추천하는 방식으로 발전시킬 수 있다.

즉, 지금 공부한 배열, 2차원 배열, 중첩 for문, 향상된 for문은 패션 추천 시스템에서 다음 기능으로 연결될 수 있다.

```text
1. 여러 옷 목록 저장
2. 여러 추천 점수 저장
3. 여러 코디 후보 관리
4. 코디별 점수 계산
5. 평균 점수 계산
6. 가장 좋은 코디 찾기
7. 사용자에게 추천 결과 출력
```

---

## 34. 복학 전 공부 흐름에서의 의미

지금은 휴학 중이고 복학 전까지 Java 기본기를 다시 잡는 과정이다.

배열은 앞으로 메서드, 객체지향, 자료구조를 공부할 때 계속 나온다.

특히 배열은 반복문과 함께 이해해야 한다.

오늘 이해한 핵심은 다음이다.

```text
배열은 여러 값을 담는 공간이다.
반복문은 배열의 값을 하나씩 꺼내는 도구이다.
students.length는 배열 길이이다.
total = 0은 합계를 담기 위한 빈 바구니이다.
2차원 배열은 행과 열로 접근한다.
arr.length는 행의 개수이다.
arr[row].length는 현재 행의 열 개수이다.
향상된 for문은 배열 값을 처음부터 끝까지 읽을 때 편하다.
인덱스가 필요하면 일반 for문을 써야 한다.
```

이 내용을 이해하면 앞으로 배열 문제를 볼 때 코드 구조를 더 잘 잡을 수 있을 것 같다.

---

## 35. 다음 공부 계획

다음에는 배열 문제와 풀이를 더 풀어보면서,
배열과 반복문을 연결하는 연습을 해야겠다.

특히 다음을 더 연습해야겠다.

```text
1. 배열의 총합 구하기
2. 배열의 평균 구하기
3. 배열에서 최댓값 찾기
4. 배열에서 최솟값 찾기
5. 향상된 for문으로 배열 전체 탐색하기
6. 인덱스가 필요한 문제와 필요 없는 문제 구분하기
7. 2차원 배열에서 행과 열 구분하기
```

코드를 바로 외우기보다,
배열에 무엇이 들어 있고,
반복문이 어떤 순서로 배열을 방문하는지 먼저 생각해야겠다.