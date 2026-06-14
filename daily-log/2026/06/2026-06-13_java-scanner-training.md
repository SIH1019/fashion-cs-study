# 2026-06-13 Java Scanner 훈련 정리

## 1. 오늘 공부한 내용

오늘은 Java 입문 강의의 `훈련` 단원에서 `Scanner`를 공부했다.

이번 단원은 지금까지 배운 변수, 연산자, 조건문, 반복문을 실제 입력 프로그램에 적용해보는 내용이었다.

공부한 내용은 다음과 같다.

- `Scanner`를 사용하는 이유
- 사용자 입력을 받는 방법
- `nextLine()`, `nextInt()` 사용
- 입력받은 값을 변수에 저장하는 흐름
- Scanner와 조건문 연결
- Scanner와 반복문 연결
- `while(true)`를 쓰는 이유
- `break`로 반복문을 빠져나가는 구조
- 이름과 나이 반복 입력 문제
- 상품 가격 계산 문제
- 여러 숫자의 합계와 평균 계산 문제
- 내가 헷갈린 부분: 왜 반복문을 써야 하는지, 왜 `while(true)`인지

이번 단원은 단순히 문법을 외우는 내용이 아니라,
사용자가 입력하는 값에 따라 프로그램이 다르게 동작하도록 만드는 연습이었다.

---

## 2. Scanner란?

`Scanner`는 사용자의 입력을 받기 위해 사용하는 Java의 기능이다.

지금까지는 코드 안에 값을 직접 적어두고 출력했다.

예를 들어 다음처럼 작성했다.

```java
int age = 20;
System.out.println(age);
```

이 코드는 항상 20만 출력한다.

그런데 실제 프로그램에서는 사용자가 직접 값을 입력해야 하는 경우가 많다.

예를 들어 이름, 나이, 가격, 수량, 메뉴 번호 같은 값은 사용자가 직접 입력해야 한다.

이때 사용하는 것이 `Scanner`이다.

---

## 3. Scanner 기본 사용법

`Scanner`를 사용하려면 먼저 import가 필요하다.

```java
import java.util.Scanner;
```

그리고 `main` 메서드 안에서 Scanner 객체를 만든다.

```java
Scanner scanner = new Scanner(System.in);
```

전체 구조는 다음과 같다.

```java
package scanner;

import java.util.Scanner;

public class Scanner1 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("문자열을 입력하세요: ");
        String str = scanner.nextLine();

        System.out.println("입력한 문자열: " + str);
    }
}
```

여기서 중요한 코드는 다음이다.

```java
Scanner scanner = new Scanner(System.in);
```

이 코드는 사용자 입력을 받을 준비를 하는 코드이다.

`System.in`은 사용자가 키보드로 입력하는 값을 의미한다.

---

## 4. nextLine()과 nextInt()

Scanner에서 자주 사용하는 입력 메서드는 다음과 같다.

```java
nextLine()
nextInt()
```

## nextLine()

`nextLine()`은 문자열 한 줄을 입력받는다.

```java
String name = scanner.nextLine();
```

사용자가 입력한 문장을 문자열로 저장한다.

예를 들어 사용자가 `송인혜`라고 입력하면,
`name` 변수에 `"송인혜"`가 저장된다.

---

## nextInt()

`nextInt()`는 정수를 입력받는다.

```java
int age = scanner.nextInt();
```

사용자가 `22`를 입력하면,
`age` 변수에 정수 22가 저장된다.

---

## 5. Scanner를 사용할 때 중요한 흐름

Scanner 문제는 보통 다음 흐름으로 생각하면 된다.

```text
1. 사용자에게 입력 안내 문구를 출력한다.
2. Scanner로 값을 입력받는다.
3. 입력받은 값을 변수에 저장한다.
4. 저장한 값을 조건문이나 계산에 사용한다.
5. 결과를 출력한다.
```

예를 들어 이름과 나이를 입력받는다면 다음 흐름이다.

```java
System.out.print("이름을 입력하세요: ");
String name = scanner.nextLine();

System.out.print("나이를 입력하세요: ");
int age = scanner.nextInt();

System.out.println("입력한 이름: " + name + ", 나이: " + age);
```

여기서 `name`과 `age`는 사용자가 입력한 값을 저장하는 변수이다.

---

## 6. Scanner와 조건문

사용자 입력을 받으면 조건문과 연결할 수 있다.

예를 들어 사용자가 입력한 나이가 18 이상이면 성인,
18 미만이면 미성년자로 출력할 수 있다.

```java
Scanner scanner = new Scanner(System.in);

System.out.print("나이를 입력하세요: ");
int age = scanner.nextInt();

if (age >= 18) {
    System.out.println("성인입니다.");
} else {
    System.out.println("미성년자입니다.");
}
```

이 코드는 사용자가 어떤 값을 입력하느냐에 따라 결과가 달라진다.

즉, Scanner는 프로그램을 고정된 결과가 아니라 사용자 입력에 따라 달라지는 프로그램으로 만들어준다.

---

## 7. Scanner와 반복문

Scanner 문제에서 반복문이 필요한 이유는 사용자의 입력을 여러 번 받아야 하는 경우가 있기 때문이다.

예를 들어 숫자 하나만 입력받는다면 반복문이 필요 없다.

```java
int number = scanner.nextInt();
```

하지만 숫자를 계속 입력받아야 한다면 같은 코드를 계속 반복해야 한다.

```java
System.out.print("숫자를 입력하세요: ");
int number = scanner.nextInt();

System.out.print("숫자를 입력하세요: ");
number = scanner.nextInt();

System.out.print("숫자를 입력하세요: ");
number = scanner.nextInt();
```

이렇게 직접 여러 번 쓰는 방식은 좋지 않다.

왜냐하면 몇 번 입력받아야 할지 모르는 문제에서는 코드를 미리 몇 줄 써야 할지 알 수 없기 때문이다.

그래서 반복문을 사용한다.

---

## 8. 내가 헷갈렸던 부분

내가 헷갈렸던 부분은 이것이다.

```text
왜 굳이 while(true)를 쓰는지 모르겠다.
그냥 반복문 안 쓰고 입력받으면 되는 것 아닌가?
```

처음에는 입력을 한 번 받고,
조건문으로 처리하면 된다고 생각했다.

하지만 문제에서 중요한 표현은 다음이었다.

```text
여러 개의 숫자를 입력받는다.
사용자가 -1을 입력하면 종료한다.
```

여기서 핵심은 `여러 개`이다.

여러 개인데 몇 개인지 정해져 있지 않다.

사용자가 숫자를 3개 입력할 수도 있고,
5개 입력할 수도 있고,
100개 입력할 수도 있다.

즉, 입력 횟수를 미리 알 수 없다.

그래서 반복문이 필요하다.

---

## 9. 반복문을 안 쓰면 생기는 문제

반복문을 안 쓰면 입력 횟수를 내가 직접 정해야 한다.

예를 들어 이렇게 쓰면 숫자를 3번만 입력받는 코드가 된다.

```java
int num1 = scanner.nextInt();
int num2 = scanner.nextInt();
int num3 = scanner.nextInt();
```

그런데 문제는 숫자 3개를 입력받으라는 문제가 아니다.

문제는 다음과 같다.

```text
숫자를 여러 개 입력받고,
-1을 입력하면 종료한다.
```

그러면 사용자가 언제 `-1`을 입력할지 모른다.

예를 들어 사용자가 이렇게 입력할 수도 있다.

```text
10
20
-1
```

이 경우 실제 숫자는 2개만 입력한 것이다.

또 이렇게 입력할 수도 있다.

```text
1
2
3
4
5
-1
```

이 경우 실제 숫자는 5개이다.

입력 개수가 매번 달라질 수 있으므로,
반복문 없이 미리 입력 코드를 정해두는 방식은 맞지 않다.

---

## 10. while(true)를 쓰는 이유

`while(true)`는 조건이 항상 참이기 때문에 계속 반복한다.

처음에는 이게 이상하게 느껴졌다.

하지만 Scanner 문제에서는 이 구조가 자연스럽다.

이유는 다음과 같다.

```text
몇 번 반복할지 모른다.
대신 종료 조건은 정해져 있다.
그러면 일단 계속 반복하고,
반복문 안에서 종료 조건을 검사하면 된다.
```

즉, `while(true)`는 무작정 무한 반복을 하려고 쓰는 것이 아니다.

정확히는 다음 뜻이다.

```text
사용자가 언제 끝낼지 모르니까 일단 계속 입력받는다.
대신 종료 값이 들어오면 break로 빠져나간다.
```

그래서 구조는 다음과 같다.

```java
while (true) {
    int input = scanner.nextInt();

    if (input == -1) {
        break;
    }

    // -1이 아닐 때 실행할 코드
}
```

---

## 11. while(true)와 break의 역할

`while(true)`와 `break`는 같이 이해해야 한다.

```java
while (true) {
```

이 코드는 일단 계속 반복하겠다는 뜻이다.

```java
if (input == -1) {
    break;
}
```

이 코드는 사용자가 종료 값을 입력하면 반복문을 빠져나가겠다는 뜻이다.

정리하면 다음과 같다.

```text
while(true)
→ 계속 입력받게 만드는 장치

if (input == -1)
→ 사용자가 종료하겠다고 했는지 확인하는 장치

break
→ 종료 조건을 만족하면 반복문을 끝내는 장치
```

그러니까 `while(true)`는 혼자 쓰는 것이 아니라,
반드시 반복문 안에 종료 조건과 `break`가 있어야 한다.

---

## 12. 문제 문장을 코드로 바꾸는 방법

문제 문장:

```text
사용자로부터 여러 개의 숫자를 입력 받고,
마지막에는 -1을 입력하여 숫자 입력을 종료한다고 가정합니다.
모든 숫자의 입력이 끝난 후 합계와 평균을 출력하세요.
```

이 문장을 코드 구조로 바꾸면 다음과 같다.

```text
여러 개의 숫자를 입력받는다.
→ 몇 개인지 모른다.
→ while(true)

숫자를 하나 입력받는다.
→ input = scanner.nextInt();

-1이면 종료한다.
→ if (input == -1) break;

-1이 아니면 합계에 더한다.
→ sum += input;

평균을 구하려면 입력 개수가 필요하다.
→ count++;

반복이 끝나면 합계와 평균을 출력한다.
→ System.out.println(sum);
→ System.out.println(average);
```

이렇게 문제 문장을 코드 역할로 나눠서 생각하면 된다.

---

## 13. 여러 숫자의 합계와 평균 문제 코드

```java
package scanner.ex;

import java.util.Scanner;

public class ScannerWhileEx3 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int sum = 0;
        int count = 0;
        int input = 0;

        System.out.println("숫자를 입력하세요. 입력을 중단하려면 -1을 입력하세요:");

        while (true) {
            input = scanner.nextInt();

            if (input == -1) {
                break;
            }

            sum += input;
            count++;
        }

        double average = (double) sum / count;

        System.out.println("입력한 숫자들의 합계: " + sum);
        System.out.println("입력한 숫자들의 평균: " + average);
    }
}
```

---

## 14. 코드 분석

```java
Scanner scanner = new Scanner(System.in);
```

사용자 입력을 받기 위해 Scanner를 만든다.

---

```java
int sum = 0;
```

입력받은 숫자들의 합계를 저장하는 변수이다.

처음에는 아무 숫자도 더하지 않았으므로 0으로 시작한다.

---

```java
int count = 0;
```

입력받은 숫자의 개수를 세는 변수이다.

평균을 구하려면 몇 개의 숫자를 입력했는지 알아야 한다.

그래서 숫자를 하나 입력받을 때마다 `count++`를 한다.

---

```java
int input = 0;
```

사용자가 입력한 숫자를 저장하는 변수이다.

---

```java
while (true) {
```

몇 개의 숫자를 입력받을지 모르기 때문에 일단 계속 반복한다.

사용자가 `-1`을 입력하면 그때 멈출 것이다.

---

```java
input = scanner.nextInt();
```

사용자로부터 숫자 하나를 입력받는다.

---

```java
if (input == -1) {
    break;
}
```

입력받은 숫자가 `-1`이면 반복문을 끝낸다.

여기서 `-1`은 계산에 포함되는 숫자가 아니라 종료 신호이다.

그래서 `sum += input`보다 먼저 검사해야 한다.

만약 `sum += input`을 먼저 하면 `-1`도 합계에 들어가서 틀린다.

---

```java
sum += input;
```

입력값이 `-1`이 아니라면 실제 숫자이므로 합계에 더한다.

---

```java
count++;
```

입력값이 `-1`이 아니라면 실제 숫자 하나를 입력한 것이므로 개수를 1 증가시킨다.

---

```java
double average = (double) sum / count;
```

평균을 구한다.

여기서 `(double)`을 붙이는 이유는 소수점까지 정확히 구하기 위해서이다.

`sum`과 `count`가 둘 다 `int`이면 `int / int` 계산이 되어 소수점이 버려질 수 있다.

그래서 `sum`을 먼저 `double`로 바꿔서 실수 계산이 되도록 한다.

---

## 15. 왜 -1 검사를 먼저 해야 할까?

다음 순서가 중요하다.

```java
input = scanner.nextInt();

if (input == -1) {
    break;
}

sum += input;
count++;
```

`-1`은 사용자가 입력을 끝내겠다는 신호이다.

그러므로 합계와 개수에 포함하면 안 된다.

만약 다음처럼 작성하면 틀린다.

```java
sum += input;
count++;

if (input == -1) {
    break;
}
```

이렇게 하면 `-1`도 합계에 더해지고,
개수에도 포함된다.

그래서 종료 조건 검사는 계산보다 먼저 해야 한다.

---

## 16. 이름과 나이 반복 입력 문제

이 문제는 사용자가 이름과 나이를 반복해서 입력하고,
이름에 `"종료"`를 입력하면 프로그램을 종료하는 문제이다.

문제의 핵심 문장은 다음과 같다.

```text
사용자로부터 이름과 나이를 반복해서 입력받는다.
사용자가 "종료"를 입력하면 프로그램이 종료되어야 한다.
```

여기서도 반복 횟수가 정해져 있지 않다.

몇 명의 이름과 나이를 입력할지 모른다.

그래서 `while(true)`를 사용한다.

---

## 17. 이름과 나이 반복 입력 코드

```java
package scanner.ex;

import java.util.Scanner;

public class ScannerWhileEx1 {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        while (true) {
            System.out.print("이름을 입력하세요 (종료를 입력하면 종료): ");
            String name = input.nextLine();

            if (name.equals("종료")) {
                System.out.println("프로그램을 종료합니다.");
                break;
            }

            System.out.print("나이를 입력하세요: ");
            int age = input.nextInt();
            input.nextLine();

            System.out.println("입력한 이름: " + name + ", 나이: " + age);
        }
    }
}
```

---

## 18. 이름과 나이 코드 분석

```java
while (true) {
```

몇 명을 입력받을지 모르기 때문에 계속 반복한다.

---

```java
String name = input.nextLine();
```

이름을 입력받는다.

---

```java
if (name.equals("종료")) {
    System.out.println("프로그램을 종료합니다.");
    break;
}
```

입력한 이름이 `"종료"`이면 반복문을 빠져나간다.

문자열 비교는 `==`가 아니라 `.equals()`를 사용한다.

그래서 다음처럼 작성한다.

```java
name.equals("종료")
```

---

```java
int age = input.nextInt();
input.nextLine();
```

나이를 정수로 입력받는다.

그 다음 `input.nextLine()`을 한 번 더 사용하는 이유는,
`nextInt()`가 숫자만 가져가고 줄바꿈은 남겨둘 수 있기 때문이다.

그 줄바꿈을 처리하지 않으면 다음 `nextLine()`이 제대로 입력을 받지 못할 수 있다.

---

## 19. 상품 가격 계산 문제

상품 가격 계산 문제도 반복문을 사용한다.

문제의 핵심은 다음과 같다.

```text
상품의 가격과 수량을 입력받고 총 비용을 출력한다.
-1을 입력하여 가격 입력을 종료한다.
```

여기서도 상품을 몇 번 입력할지 모른다.

사용자가 상품 가격을 2번 입력할 수도 있고,
10번 입력할 수도 있다.

종료 조건은 가격에 `-1`을 입력하는 것이다.

그래서 `while(true)` 안에서 가격을 입력받고,
가격이 `-1`이면 종료한다.

---

## 20. 상품 가격 계산 코드 구조

```java
while (true) {
    System.out.print("상품의 가격을 입력하세요 (-1을 입력하면 종료): ");
    int price = input.nextInt();

    if (price == -1) {
        System.out.println("프로그램을 종료합니다.");
        break;
    }

    System.out.print("구매하려는 수량을 입력하세요: ");
    int quantity = input.nextInt();

    int totalCost = price * quantity;
    System.out.println("총 비용: " + totalCost);
}
```

이 문제에서도 `-1`은 상품 가격이 아니라 종료 신호이다.

그래서 가격을 입력받자마자 먼저 검사해야 한다.

---

## 21. while(true)를 쓰는 문제의 공통점

`while(true)`를 쓰는 문제들은 공통점이 있다.

```text
1. 반복 횟수가 정해져 있지 않다.
2. 사용자가 언제 끝낼지 모른다.
3. 종료 신호가 따로 있다.
4. 일단 계속 입력받아야 한다.
5. 종료 신호가 들어오면 break로 빠져나간다.
```

예를 들면 다음과 같다.

```text
exit을 입력하면 종료
0을 입력하면 종료
-1을 입력하면 종료
"종료"를 입력하면 종료
메뉴에서 4번을 선택하면 종료
```

이런 문제는 반복 횟수보다 종료 조건이 중요하다.

그래서 `while(true)`와 `break` 구조를 사용한다.

---

## 22. for문과 while(true)의 차이

반복문을 고를 때는 문제 문장을 봐야 한다.

## for문이 자연스러운 경우

반복 횟수가 정해져 있을 때는 `for`문이 자연스럽다.

예를 들어 다음 문제이다.

```text
숫자 5개를 입력받으세요.
```

이 경우는 5번 반복하면 된다.

```java
for (int i = 0; i < 5; i++) {
    int number = scanner.nextInt();
}
```

---

## while(true)가 자연스러운 경우

반복 횟수가 정해져 있지 않고,
사용자가 특정 값을 입력할 때까지 반복해야 하면 `while(true)`가 자연스럽다.

예를 들어 다음 문제이다.

```text
숫자를 여러 개 입력받고, -1을 입력하면 종료하세요.
```

이 경우는 몇 번 반복할지 모른다.

```java
while (true) {
    int number = scanner.nextInt();

    if (number == -1) {
        break;
    }
}
```

---

## 23. 내가 오늘 이해한 핵심

오늘 내가 이해한 핵심은 다음이다.

```text
여러 개라고 했는데 몇 개인지 정해져 있지 않으면,
반복문을 써야 한다.
```

그리고 종료 조건이 따로 있으면 `while(true)`를 쓸 수 있다.

```text
여러 개라서 몇 개인지 모른다.
→ 입력을 계속 받아야 한다.
→ while(true)를 사용한다.

하지만 진짜 무한 반복되면 안 된다.
→ 종료 조건을 if문으로 검사한다.
→ 종료 값이 들어오면 break로 빠져나간다.
```

즉, `while(true)`는 그냥 무한 반복하려고 쓰는 것이 아니라,
사용자가 언제 끝낼지 모르는 상황을 처리하기 위해 쓰는 구조이다.

---

## 24. 내가 헷갈렸던 생각 정리

처음에는 반복문 없이 입력을 받으면 된다고 생각했다.

하지만 반복문 없이 입력을 받으면,
내가 입력 횟수를 미리 정해버리는 문제가 생긴다.

예를 들어 입력 코드를 3번 쓰면 3번만 입력받는 프로그램이 된다.

하지만 문제에서는 3개라고 하지 않았다.

문제에서는 여러 개라고 했고,
종료는 `-1`을 입력하면 된다고 했다.

그러면 중요한 것은 입력 개수가 아니라 종료 신호이다.

그래서 이 문제는 다음처럼 이해해야 한다.

```text
입력 개수는 모른다.
종료 신호는 안다.
그러면 계속 입력받고,
종료 신호가 들어오면 멈춘다.
```

이 구조가 바로 `while(true) + if + break`이다.

---

## 25. Scanner 문제를 풀 때 생각 순서

앞으로 Scanner 문제를 풀 때는 다음 순서로 생각하면 된다.

```text
1. 입력을 몇 번 받는 문제인지 본다.
2. 입력 횟수가 정해져 있으면 for문을 생각한다.
3. 입력 횟수가 정해져 있지 않으면 while문을 생각한다.
4. 종료 값이 있는지 찾는다.
5. 종료 값이 있으면 while(true) 안에서 if로 검사한다.
6. 종료 값이면 break로 빠져나간다.
7. 종료 값이 아니면 계산하거나 출력한다.
```

예를 들어 문제에 이런 말이 있으면 `while(true)`를 의심해야 한다.

```text
반복해서 입력받으세요
계속 입력받으세요
종료를 입력하면 끝냅니다
0을 입력하면 종료
-1을 입력하면 종료
exit을 입력하면 종료
```

---

## 26. 프로젝트와의 연결

내가 만들고 싶은 프로젝트는 패션 추천 시스템이다.

이 시스템은 사용자가 옷 정보를 입력하면,
색상, 핏, 기장, 상황, 분위기 등을 분석해서 옷 조합을 추천하고 설명하는 방향이다.

Scanner는 나중에 콘솔 버전 패션 추천 프로그램을 만들 때 사용할 수 있다.

예를 들어 사용자가 직접 옷 정보를 입력할 수 있다.

```text
상의 색상을 입력하세요: 네이비
하의 색상을 입력하세요: 블랙
신발 색상을 입력하세요: 화이트
상황을 입력하세요: 학교
```

이렇게 입력받은 값을 변수에 저장한 다음,
조건문으로 추천 결과를 만들 수 있다.

예를 들어 다음처럼 생각할 수 있다.

```java
if (topColor.equals("네이비") && bottomColor.equals("블랙")) {
    System.out.println("차분하고 시크한 조합입니다.");
}
```

또 사용자가 여러 벌의 옷을 입력할 수도 있다.

```text
옷 정보를 입력하세요.
종료하려면 exit을 입력하세요.
```

이 경우 몇 벌을 입력할지 모른다.

그러면 오늘 배운 `while(true)` 구조가 필요하다.

```java
while (true) {
    System.out.print("옷 이름을 입력하세요(exit 입력 시 종료): ");
    String itemName = scanner.nextLine();

    if (itemName.equals("exit")) {
        break;
    }

    System.out.println(itemName + "을 등록했습니다.");
}
```

즉, Scanner는 사용자의 입력을 받는 기초이고,
`while(true)`는 사용자가 원하는 만큼 옷 정보를 입력하게 만드는 구조이다.

나중에 패션 추천 콘솔 프로그램을 만들 때 다음 기능에 연결할 수 있다.

- 옷 이름 입력
- 색상 입력
- 카테고리 입력
- 상황 입력
- 여러 개의 옷 등록
- 사용자가 종료할 때까지 계속 입력
- 입력받은 옷 정보를 바탕으로 추천 결과 출력

지금은 단순히 숫자나 이름을 입력받는 문제를 풀고 있지만,
이 구조가 나중에는 패션 추천 시스템의 입력 기능으로 이어질 수 있다.

---

## 27. 오늘 공부하면서 느낀 점

오늘 Scanner 문제를 보면서 단순히 코드를 외우는 것보다,
문제 문장을 코드 구조로 바꾸는 것이 중요하다는 것을 느꼈다.

특히 `while(true)`가 처음에는 이상하게 느껴졌다.

왜 조건식에 그냥 `true`를 쓰는지 이해가 안 됐다.

그런데 문제에서 `여러 개`라고 했고,
몇 개인지 정해져 있지 않다는 점을 보고 이해했다.

반복 횟수를 모르면 일단 계속 반복해야 하고,
대신 종료 조건을 반복문 안에서 검사해야 한다.

그래서 `while(true)`를 쓰고,
`-1`, `0`, `"종료"`, `"exit"` 같은 값이 들어오면 `break`로 빠져나간다.

오늘 이해한 핵심은 다음이다.

```text
여러 개라서 몇 개인지 모른다.
그래서 while(true)를 쓴다.
종료 값이 들어오면 break로 끝낸다.
```

이제 Scanner 문제를 볼 때는 입력을 몇 번 받는지,
종료 조건이 무엇인지 먼저 확인해야겠다.

---

## 28. 다음 공부 계획

다음에는 Scanner 문제를 다시 보면서,
문제 문장을 먼저 분석하고 코드 구조를 잡는 연습을 해야겠다.

특히 다음을 구분하는 연습이 필요하다.

```text
입력 개수가 정해진 문제
→ for문

입력 개수가 정해지지 않은 문제
→ while(true) + break

종료 값이 있는 문제
→ if로 종료 조건 검사
```

그리고 이후 배열 단원으로 넘어가면,
입력받은 여러 값을 배열에 저장하는 방법도 공부해야겠다.

Scanner로 값을 입력받고,
배열에 저장하고,
반복문으로 여러 값을 처리하면
나중에 패션 추천 시스템에서 여러 옷 정보를 다루는 기초가 될 것 같다.