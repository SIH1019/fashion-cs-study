# 2026-06-18 Java 배열 사용, 리팩토링, 2차원 배열, 향상된 for문 정리

## 1. 오늘 공부한 내용

오늘은 Java 배열 단원에서 배열 사용부터 향상된 for문까지 공부했다.

공부한 내용은 다음과 같다.

- 배열에 값 넣기
- 배열 값 읽기
- 배열 인덱스
- `students.length`
- 배열과 반복문 연결
- 배열 리팩토링
- 총합과 평균 구하기
- `total = 0`의 의미
- 2차원 배열
- 2차원 배열에서 행과 열
- 2차원 배열 중첩 for문
- 값을 넣는 중첩 for문과 출력하는 중첩 for문의 차이
- 향상된 for문
- 향상된 for문을 사용할 수 있는 경우
- 향상된 for문을 사용할 수 없는 경우

이번 단원에서 중요한 것은 배열을 단순히 선언하고 생성하는 것에서 끝나는 것이 아니라,
배열 안에 있는 값을 반복문으로 처리하는 방법을 이해하는 것이었다.

특히 내가 헷갈렸던 부분은 다음이었다.

```text
1. total = 0이 무슨 뜻인지
2. students.length가 배열 길이인지
3. 2차원 배열에서 중첩 for문이 왜 두 번 나오는지
4. 두 중첩 for문이 똑같이 생겼는데 뭐가 다른지
5. 향상된 for문은 일반 for문이랑 뭐가 다른지
```

---

## 2. 배열 사용 복습

배열은 같은 타입의 값을 여러 개 저장할 때 사용한다.

예를 들어 학생 점수 5개를 저장하려면 다음처럼 배열을 만들 수 있다.

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

배열은 0번부터 시작한다.

그래서 점수가 5개 있어도 인덱스는 0부터 4까지이다.

```text
배열 길이: 5
사용 가능한 인덱스: 0, 1, 2, 3, 4
마지막 인덱스: 배열 길이 - 1
```

---

## 3. 배열에 값 넣기

배열의 특정 칸에 값을 넣으려면 인덱스를 사용한다.

```java
int[] students = new int[5];

students[0] = 90;
students[1] = 80;
students[2] = 70;
students[3] = 60;
students[4] = 50;
```

이 코드는 다음과 같은 상태를 만든다.

```text
[0] [1] [2] [3] [4]
90  80  70  60  50
```

여기서 `students[0]`은 첫 번째 학생의 점수이고,
`students[1]`은 두 번째 학생의 점수이다.

배열은 1번부터 시작하지 않고 0번부터 시작한다.

---

## 4. 배열 값 읽기

배열에 저장된 값을 읽을 때도 인덱스를 사용한다.

```java
System.out.println(students[0]);
System.out.println(students[1]);
```

예를 들어 다음 배열이 있다면:

```java
int[] students = {90, 80, 70, 60, 50};
```

다음 코드는:

```java
System.out.println(students[0]);
```

출력 결과가 다음과 같다.

```text
90
```

왜냐하면 `students[0]`에는 90이 들어있기 때문이다.

---

## 5. students.length

`students.length`는 배열의 길이를 의미한다.

```java
int[] students = {90, 80, 70, 60, 50};
```

이 배열에는 값이 5개 들어있다.

그래서:

```java
students.length
```

의 값은 5이다.

정리하면 다음과 같다.

```text
students.length
→ students 배열의 길이
→ 배열 안에 몇 개의 칸이 있는지 알려줌
→ 여기서는 5
```

중요한 점은 `students.length`가 마지막 인덱스가 아니라는 것이다.

```text
students.length = 5
마지막 인덱스 = 4
```

배열 인덱스는 0부터 시작하기 때문에,
배열 길이가 5이면 마지막 인덱스는 5가 아니라 4이다.

---

## 6. 배열과 for문

배열은 반복문과 같이 사용할 때 편리하다.

학생 점수 5개를 출력한다고 하면 직접 이렇게 쓸 수 있다.

```java
System.out.println(students[0]);
System.out.println(students[1]);
System.out.println(students[2]);
System.out.println(students[3]);
System.out.println(students[4]);
```

하지만 이 방식은 반복이 너무 많다.

배열과 for문을 사용하면 다음처럼 줄일 수 있다.

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

`students.length`가 5이므로,
실제로는 다음과 같다.

```java
i < 5
```

그래서 `i`는 0, 1, 2, 3, 4까지만 반복한다.

---

## 7. 왜 i <= students.length가 아니라 i < students.length일까?

배열 길이가 5이면 사용할 수 있는 인덱스는 0부터 4까지이다.

```text
students.length = 5
사용 가능한 인덱스 = 0, 1, 2, 3, 4
```

만약 조건을 이렇게 쓰면:

```java
i <= students.length
```

`i`가 5일 때도 반복문이 실행된다.

그러면 다음 코드가 실행될 수 있다.

```java
students[5]
```

하지만 `students[5]`는 존재하지 않는다.

배열의 마지막 인덱스는 4이기 때문이다.

그래서 배열 반복문에서는 보통 다음처럼 쓴다.

```java
for (int i = 0; i < students.length; i++)
```

이렇게 하면 `i`가 0부터 4까지만 실행되므로 안전하다.

---

## 8. 배열 리팩토링

리팩토링은 프로그램의 결과는 그대로 유지하면서 코드 구조를 더 좋게 바꾸는 것이다.

배열을 사용하지 않으면 학생 점수를 각각 다른 변수에 저장해야 한다.

```java
int student1 = 90;
int student2 = 80;
int student3 = 70;
int student4 = 60;
int student5 = 50;
```

하지만 배열을 사용하면 하나의 이름으로 여러 값을 관리할 수 있다.

```java
int[] students = {90, 80, 70, 60, 50};
```

그리고 반복문을 사용하면 출력 코드도 줄일 수 있다.

```java
for (int i = 0; i < students.length; i++) {
    System.out.println("학생" + (i + 1) + " 점수: " + students[i]);
}
```

여기서 `i + 1`을 쓰는 이유는 학생 번호는 1번부터 출력하고 싶기 때문이다.

```text
i = 0 → 학생1
i = 1 → 학생2
i = 2 → 학생3
```

배열 인덱스는 0부터 시작하지만,
사람에게 보여주는 학생 번호는 1부터 시작하는 것이 자연스럽다.

---

## 9. 배열 초기화 간단히 하기

배열은 다음처럼 생성하고 값을 따로 넣을 수 있다.

```java
int[] students = new int[5];

students[0] = 90;
students[1] = 80;
students[2] = 70;
students[3] = 60;
students[4] = 50;
```

하지만 처음부터 값을 알고 있다면 더 짧게 쓸 수 있다.

```java
int[] students = {90, 80, 70, 60, 50};
```

이 코드는 배열을 만들면서 동시에 값을 넣는 방식이다.

즉, 다음과 같은 배열이 만들어진다.

```text
[0] [1] [2] [3] [4]
90  80  70  60  50
```

---

## 10. 총합 구하기 문제

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

## 11. total = 0의 의미

```java
int total = 0;
```

`total`은 점수들을 하나씩 더해서 누적할 변수이다.

내가 이해한 것처럼 `total = 0`은 빈 바구니라고 생각하면 된다.

처음에는 아무 점수도 더하지 않았으므로 0에서 시작한다.

```text
total
→ 점수들을 담을 빈 바구니
→ 처음에는 아무것도 안 더했으니까 0
```

이후 반복문을 돌면서 점수를 하나씩 더한다.

```java
total += students[i];
```

이 코드는 다음과 같다.

```java
total = total + students[i];
```

즉, 기존 total에 현재 학생 점수를 더해서 다시 total에 저장하는 것이다.

---

## 12. total 값이 변하는 과정

배열은 다음과 같다.

```java
int[] students = {90, 80, 70, 60, 50};
```

반복문은 다음과 같다.

```java
for (int i = 0; i < students.length; i++) {
    total += students[i];
}
```

실행 과정은 다음과 같다.

```text
처음:
total = 0

i = 0:
students[0] = 90
total = total + students[0]
total = 0 + 90
total = 90

i = 1:
students[1] = 80
total = total + students[1]
total = 90 + 80
total = 170

i = 2:
students[2] = 70
total = total + students[2]
total = 170 + 70
total = 240

i = 3:
students[3] = 60
total = total + students[3]
total = 240 + 60
total = 300

i = 4:
students[4] = 50
total = total + students[4]
total = 300 + 50
total = 350
```

반복문이 끝나면 최종적으로 다음 상태가 된다.

```text
total = 350
```

---

## 13. 평균 구하기

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

여기서 `(double) total`을 쓰는 이유는 평균이 소수점까지 나올 수 있기 때문이다.

만약 점수 합계가 351이고 학생 수가 5명이면 평균은 다음과 같다.

```text
351 / 5 = 70.2
```

그런데 `int / int`로 계산하면 소수점이 버려질 수 있다.

그래서 `total`을 먼저 `double`로 바꿔서 실수 계산이 되도록 한다.

```java
(double) total / students.length
```

---

## 14. 2차원 배열

지금까지 사용한 배열은 1차원 배열이다.

1차원 배열은 값이 한 줄로 나열된 구조이다.

```java
int[] students = {90, 80, 70, 60, 50};
```

그림으로 보면 다음과 같다.

```text
[0] [1] [2] [3] [4]
90  80  70  60  50
```

2차원 배열은 행과 열로 구성된 배열이다.

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

## 15. 행과 열

2차원 배열에서는 행과 열을 사용한다.

```text
행 → row
열 → column
```

2차원 배열은 다음처럼 접근한다.

```java
arr[row][column]
```

예를 들어:

```java
arr[0][0]
```

은 0행 0열이다.

```java
arr[1][2]
```

은 1행 2열이다.

정리하면 다음과 같다.

```text
arr[0][0] → 0행 0열
arr[0][1] → 0행 1열
arr[0][2] → 0행 2열
arr[1][0] → 1행 0열
arr[1][1] → 1행 1열
arr[1][2] → 1행 2열
```

---

## 16. 2차원 배열에 값 직접 넣기

2차원 배열에 값을 직접 넣으면 다음과 같다.

```java
int[][] arr = new int[2][3];

arr[0][0] = 1;
arr[0][1] = 2;
arr[0][2] = 3;
arr[1][0] = 4;
arr[1][1] = 5;
arr[1][2] = 6;
```

배열 상태는 다음과 같다.

```text
1 2 3
4 5 6
```

하지만 이렇게 직접 쓰면 코드가 길어진다.

그래서 중첩 for문으로 줄일 수 있다.

---

## 17. 2차원 배열과 중첩 for문

2차원 배열은 행과 열이 있기 때문에 중첩 for문을 사용한다.

바깥 for문은 행을 담당하고,
안쪽 for문은 열을 담당한다.

```java
for (int row = 0; row < arr.length; row++) {
    for (int column = 0; column < arr[row].length; column++) {
        // arr[row][column] 사용
    }
}
```

역할은 다음과 같다.

```text
row
→ 몇 번째 행인지

column
→ 그 행에서 몇 번째 열인지
```

예를 들어 2행 3열 배열에서는 다음 순서로 이동한다.

```text
row = 0, column = 0 → arr[0][0]
row = 0, column = 1 → arr[0][1]
row = 0, column = 2 → arr[0][2]

row = 1, column = 0 → arr[1][0]
row = 1, column = 1 → arr[1][1]
row = 1, column = 2 → arr[1][2]
```

---

## 18. 2차원 배열 자동 입력 코드

내가 질문한 코드는 다음과 같다.

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

이 코드는 크게 두 부분으로 나뉜다.

```text
1. 배열에 값을 넣는 중첩 for문
2. 배열의 값을 출력하는 중첩 for문
```

---

## 19. 첫 번째 중첩 for문: 값 넣기

첫 번째 중첩 for문은 다음과 같다.

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

처음 `i`는 1이다.

실행 흐름은 다음과 같다.

```text
arr[0][0] = 1
arr[0][1] = 2
arr[0][2] = 3
arr[1][0] = 4
arr[1][1] = 5
arr[1][2] = 6
```

결과적으로 배열은 다음 상태가 된다.

```text
1 2 3
4 5 6
```

하지만 이 시점에서는 아직 화면에 출력된 것이 아니다.

배열 안에 값만 저장된 상태이다.

---

## 20. i++의 의미

```java
arr[row][column] = i++;
```

여기서 `i++`는 후위 증가 연산자이다.

즉, 먼저 현재 i 값을 사용하고,
그 다음 i를 1 증가시킨다.

예를 들어 처음 `i = 1`이면:

```text
arr[0][0] = i++;
→ arr[0][0]에 1을 넣음
→ 그 다음 i는 2가 됨
```

다음 칸에서는 `i = 2`가 된다.

```text
arr[0][1] = i++;
→ arr[0][1]에 2를 넣음
→ 그 다음 i는 3이 됨
```

그래서 배열에 1, 2, 3, 4, 5, 6이 순서대로 들어간다.

---

## 21. 두 번째 중첩 for문: 출력하기

두 번째 중첩 for문은 다음과 같다.

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

이 코드는 현재 배열 칸의 값을 읽어서 출력한다.

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

둘 다 2차원 배열 전체를 한 칸씩 방문해야 하기 때문에 모양이 같다.

하지만 안에서 하는 일이 다르다.

첫 번째 중첩 for문:

```java
arr[row][column] = i++;
```

역할:

```text
배열에 값을 넣는다.
배열 상태를 바꾼다.
화면 출력은 하지 않는다.
```

두 번째 중첩 for문:

```java
System.out.print(arr[row][column] + " ");
```

역할:

```text
배열에 저장된 값을 읽는다.
화면에 출력한다.
배열 상태는 바꾸지 않는다.
```

정리하면 다음과 같다.

```text
첫 번째 중첩 for문
→ 저장용

두 번째 중첩 for문
→ 출력용
```

두 반복문이 똑같이 생긴 이유는 둘 다 같은 배열의 모든 칸을 방문해야 하기 때문이다.

차이는 안쪽 코드이다.

```text
arr[row][column] = i++;
→ 값 넣기

System.out.print(arr[row][column] + " ");
→ 값 출력하기
```

---

## 23. arr.length와 arr[row].length

2차원 배열에서 길이를 볼 때는 두 가지가 나온다.

```java
arr.length
```

이것은 행의 개수이다.

```java
int[][] arr = new int[2][3];
```

여기서 `arr.length`는 2이다.

```text
arr.length = 2
```

왜냐하면 2행짜리 배열이기 때문이다.

반면:

```java
arr[row].length
```

이것은 현재 행의 열 개수이다.

`new int[2][3]`에서는 각 행마다 열이 3개이다.

그래서:

```text
arr[0].length = 3
arr[1].length = 3
```

정리하면 다음과 같다.

```text
arr.length
→ 행의 개수

arr[row].length
→ 현재 row 행의 열 개수
```

---

## 24. 향상된 for문

향상된 for문은 배열을 처음부터 끝까지 순서대로 탐색할 때 사용하는 편리한 for문이다.

다른 말로 for-each문이라고도 한다.

기본 구조는 다음과 같다.

```java
for (변수 : 배열) {
    // 반복할 코드
}
```

예를 들어 배열이 있다.

```java
int[] numbers = {1, 2, 3, 4, 5};
```

일반 for문으로 출력하면 다음과 같다.

```java
for (int i = 0; i < numbers.length; i++) {
    int number = numbers[i];
    System.out.println(number);
}
```

향상된 for문으로 바꾸면 다음과 같다.

```java
for (int number : numbers) {
    System.out.println(number);
}
```

---

## 25. 향상된 for문 읽는 방법

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

즉, 향상된 for문은 인덱스를 직접 쓰지 않아도 배열의 값을 하나씩 꺼내준다.

---

## 26. 일반 for문과 향상된 for문 비교

일반 for문:

```java
for (int i = 0; i < numbers.length; i++) {
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

둘은 결과가 같다.

하지만 일반 for문은 인덱스 `i`를 직접 관리해야 한다.

```text
int i = 0
i < numbers.length
i++
numbers[i]
```

반면 향상된 for문은 이런 부분을 직접 쓰지 않아도 된다.

```text
배열에서 값을 하나씩 꺼내서 number에 담아줌
```

그래서 단순히 배열의 값을 처음부터 끝까지 읽기만 할 때는 향상된 for문이 더 간단하다.

---

## 27. 향상된 for문을 사용할 수 있는 경우

향상된 for문은 배열의 모든 값을 순서대로 읽을 때 사용하기 좋다.

예를 들어 점수 배열의 모든 값을 출력할 때 사용할 수 있다.

```java
int[] students = {90, 80, 70, 60, 50};

for (int score : students) {
    System.out.println(score);
}
```

실행 결과:

```text
90
80
70
60
50
```

또 총합을 구할 때도 사용할 수 있다.

```java
int[] students = {90, 80, 70, 60, 50};

int total = 0;

for (int score : students) {
    total += score;
}

System.out.println("점수 총합: " + total);
```

여기서 `score`는 배열에서 하나씩 꺼낸 점수이다.

실행 흐름은 다음과 같다.

```text
score = 90 → total = 0 + 90
score = 80 → total = 90 + 80
score = 70 → total = 170 + 70
score = 60 → total = 240 + 60
score = 50 → total = 300 + 50
```

최종 결과:

```text
total = 350
```

---

## 28. 향상된 for문으로 평균 구하기

학생 점수의 평균도 향상된 for문으로 구할 수 있다.

```java
package array.ex;

public class ArrayEx1 {
    public static void main(String[] args) {
        int[] students = {90, 80, 70, 60, 50};

        int total = 0;

        for (int score : students) {
            total += score;
        }

        double average = (double) total / students.length;

        System.out.println("점수 총합: " + total);
        System.out.println("점수 평균: " + average);
    }
}
```

여기서 `students.length`는 여전히 배열 길이이다.

```text
students.length = 5
```

향상된 for문은 배열의 값을 하나씩 꺼내는 데 사용하고,
평균을 구할 때는 학생 수가 필요하므로 `students.length`를 사용한다.

---

## 29. 향상된 for문을 사용할 수 없는 경우

향상된 for문은 편하지만 항상 사용할 수 있는 것은 아니다.

향상된 for문은 인덱스를 직접 다루지 않는다.

그래서 인덱스 번호가 필요한 경우에는 일반 for문을 사용하는 것이 좋다.

예를 들어 다음처럼 학생 번호를 같이 출력해야 한다고 해보자.

```text
학생1 점수: 90
학생2 점수: 80
학생3 점수: 70
```

이 경우에는 인덱스 `i`가 필요하다.

일반 for문:

```java
for (int i = 0; i < students.length; i++) {
    System.out.println("학생" + (i + 1) + " 점수: " + students[i]);
}
```

향상된 for문은 `i`가 없기 때문에 학생 번호를 자연스럽게 만들기 어렵다.

억지로 다음처럼 할 수는 있다.

```java
int i = 0;
for (int score : students) {
    System.out.println("학생" + (i + 1) + " 점수: " + score);
    i++;
}
```

하지만 이렇게 할 거면 일반 for문을 쓰는 것이 더 깔끔하다.

---

## 30. 일반 for문을 써야 하는 경우

다음과 같은 경우에는 일반 for문이 더 좋다.

```text
1. 인덱스 번호가 필요할 때
2. 특정 위치의 값을 바꿔야 할 때
3. 앞뒤 값을 비교해야 할 때
4. 배열을 거꾸로 탐색해야 할 때
5. 일부 구간만 탐색해야 할 때
```

예를 들어 배열 값을 직접 바꿀 때는 일반 for문이 더 자연스럽다.

```java
for (int i = 0; i < students.length; i++) {
    students[i] = students[i] + 10;
}
```

이 코드는 각 학생 점수에 10점을 더한다.

향상된 for문은 값을 읽는 데는 편하지만,
인덱스를 기준으로 배열 칸을 직접 수정해야 할 때는 일반 for문이 더 적합하다.

---

## 31. 일반 for문과 향상된 for문 선택 기준

정리하면 다음과 같다.

```text
배열의 값을 처음부터 끝까지 단순히 읽기만 한다.
→ 향상된 for문 사용 가능

배열의 인덱스가 필요하다.
→ 일반 for문 사용

배열의 특정 위치를 수정해야 한다.
→ 일반 for문 사용

학생1, 학생2처럼 번호가 필요하다.
→ 일반 for문 사용

배열의 모든 값을 더한다.
→ 향상된 for문 사용 가능
```

예시:

```java
for (int score : students) {
    total += score;
}
```

이 코드는 점수를 하나씩 꺼내서 더하기만 하므로 향상된 for문이 잘 맞는다.

반면:

```java
for (int i = 0; i < students.length; i++) {
    System.out.println("학생" + (i + 1) + " 점수: " + students[i]);
}
```

이 코드는 학생 번호를 만들기 위해 `i`가 필요하므로 일반 for문이 더 좋다.

---

## 32. 오늘 헷갈렸던 부분 정리

오늘 헷갈렸던 부분은 다음이었다.

```text
1. total = 0은 무슨 뜻인가?
2. students.length는 배열 길이가 맞는가?
3. 2차원 배열에서 중첩 for문이 왜 두 번 나오는가?
4. 두 중첩 for문은 똑같이 생겼는데 뭐가 다른가?
5. 향상된 for문은 일반 for문과 뭐가 다른가?
```

정리하면 다음과 같다.

```text
total = 0
→ 점수를 더하기 위한 빈 바구니이다.
→ 아무 점수도 더하지 않은 상태라서 0부터 시작한다.

students.length
→ students 배열의 길이이다.
→ {90, 80, 70, 60, 50}이면 길이는 5이다.

첫 번째 중첩 for문
→ 2차원 배열에 값을 넣는다.

두 번째 중첩 for문
→ 2차원 배열에 들어있는 값을 출력한다.

향상된 for문
→ 배열의 값을 처음부터 끝까지 하나씩 꺼낼 때 편하다.
→ 인덱스가 필요하면 일반 for문을 쓰는 것이 좋다.
```

---

## 33. 내가 이해한 핵심

오늘 이해한 핵심은 배열은 반복문과 같이 사용할 때 진짜 편해진다는 것이다.

배열만 사용하면 여러 값을 하나의 이름으로 묶을 수 있다.

하지만 배열에 있는 값을 하나씩 처리하려면 반복문이 필요하다.

```java
for (int i = 0; i < students.length; i++) {
    total += students[i];
}
```

이 코드는 배열의 모든 값을 하나씩 꺼내서 total에 더한다.

향상된 for문을 사용하면 더 간단하게 쓸 수 있다.

```java
for (int score : students) {
    total += score;
}
```

하지만 향상된 for문은 인덱스를 직접 사용하지 않기 때문에,
학생 번호처럼 인덱스가 필요한 경우에는 일반 for문을 사용해야 한다.

---

## 34. 내가 만들려는 프로젝트와의 연결

내가 만들고 싶은 프로젝트는 패션 추천 시스템이다.

이 시스템은 사용자가 입력한 옷 정보를 바탕으로 색상, 핏, 기장, 상황, 분위기 등을 분석해서 옷 조합을 추천하고 설명하는 방향이다.

배열과 반복문은 패션 추천 시스템에서 여러 개의 옷 정보나 점수를 처리할 때 사용할 수 있다.

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

이 코드는 색상 점수, 핏 점수, 상황 적합도 점수를 더해서 평균 추천 점수를 구하는 구조로 연결할 수 있다.

2차원 배열은 여러 코디 후보와 여러 기준 점수를 관리할 때 사용할 수 있다.

```text
          색상  핏  상황
코디1      80  70  90
코디2      90  60  85
```

이런 구조는 2차원 배열로 표현할 수 있다.

```java
int[][] outfitScores = {
    {80, 70, 90},
    {90, 60, 85}
};
```

나중에 이 배열을 반복문으로 돌면서 각 코디의 평균 점수를 계산하고,
가장 높은 점수의 코디를 추천하는 방식으로 발전시킬 수 있다.

즉, 지금 공부한 배열, 중첩 for문, 향상된 for문은 나중에 패션 추천 시스템에서 다음 기능으로 연결될 수 있다.

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

## 35. 복학 전 공부 흐름에서의 의미

지금은 휴학 중이고 복학 전까지 Java 기본기를 다시 잡는 과정이다.

배열은 앞으로 메서드, 객체지향, 자료구조를 공부할 때 계속 나온다.

특히 배열과 반복문을 연결해서 생각하는 것이 중요하다.

오늘 이해한 핵심은 다음이다.

```text
배열은 여러 값을 담는 공간이다.
반복문은 배열의 값을 하나씩 꺼내는 도구이다.
students.length는 배열 길이이다.
total = 0은 합계를 담기 위한 빈 바구니이다.
향상된 for문은 배열을 처음부터 끝까지 읽을 때 편하다.
인덱스가 필요하면 일반 for문을 써야 한다.
```

이 내용을 이해하면 앞으로 배열 문제를 볼 때 코드 구조를 더 잘 잡을 수 있을 것 같다.

---

## 36. 다음 공부 계획

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