# 2026-06-07 Java 반복문, break, continue 학습 개발일지

## 1. 오늘 공부한 주제

- 반복문
- `while`문
- `do-while`문
- 반복 조건
- 반복문 실행 흐름
- 무한 반복
- `break`
- `continue`
- `break`와 `continue`의 차이

---

## 2. 오늘 공부한 범위

- 반복문 시작
- `while`문 기본 구조
- `while`문 실행 흐름
- 반복 조건
- 반복 횟수 제어
- `do-while`문
- `while`문과 `do-while`문의 차이
- 무한 반복
- `break`
- `continue`

---

## 3. 오늘 공부하지 않은 범위

- `for`문
- 중첩 반복문
- 반복문 문제 풀이
- 배열
- 메서드
- 객체지향

---

## 4. 반복문이 필요한 이유

- 반복문은 같은 코드를 여러 번 실행할 때 사용한다.
- 같은 출력문이나 계산 코드를 계속 복사해서 쓰면 코드가 길어지고 관리하기 어렵다.
- 반복문을 사용하면 반복되는 코드를 한 번만 작성하고, 조건에 따라 여러 번 실행할 수 있다.
- 반복 횟수가 많아질수록 반복문을 사용하는 것이 훨씬 효율적이다.

예시:

```java
System.out.println(1);
System.out.println(2);
System.out.println(3);
System.out.println(4);
System.out.println(5);
```

- 위 코드는 숫자 1부터 5까지 출력한다.
- 하지만 출력해야 할 숫자가 100개라면 출력문을 100번 작성해야 한다.
- 이런 반복 작업을 줄이기 위해 반복문을 사용한다.

---

## 5. while문

```java
while (조건식) {
    실행할 코드
}
```

- `while`문은 조건식이 `true`인 동안 코드를 반복 실행한다.
- 조건식이 `true`이면 중괄호 `{}` 안의 코드가 실행된다.
- 코드 실행이 끝나면 다시 조건식으로 돌아간다.
- 조건식이 `false`가 되면 반복을 멈춘다.
- 조건식의 결과는 반드시 `true` 또는 `false`여야 한다.

---

## 6. while문 기본 예제

```java
package loop;

public class While1 {
    public static void main(String[] args) {
        int count = 0;

        while (count < 3) {
            count++;
            System.out.println("현재 숫자: " + count);
        }
    }
}
```

실행 결과:

```text
현재 숫자: 1
현재 숫자: 2
현재 숫자: 3
```

풀이:

```text
count = 0

count < 3 → true
count++ → count = 1
현재 숫자: 1 출력

count < 3 → true
count++ → count = 2
현재 숫자: 2 출력

count < 3 → true
count++ → count = 3
현재 숫자: 3 출력

count < 3 → false
반복 종료
```

---

## 7. while문 실행 흐름

- 1단계
  - 조건식을 검사한다.

- 2단계
  - 조건식이 `true`이면 반복문 내부 코드를 실행한다.

- 3단계
  - 반복문 내부 코드가 끝나면 다시 조건식으로 돌아간다.

- 4단계
  - 조건식이 `false`가 되면 반복문을 종료한다.

정리:

```text
조건식 검사
→ true이면 코드 실행
→ 다시 조건식 검사
→ false이면 반복 종료
```

---

## 8. 반복 횟수 제어

- 반복문을 사용할 때는 반복이 언제 끝날지 정해야 한다.
- 보통 반복 횟수를 세기 위해 변수를 사용한다.
- 반복 조건에 사용되는 변수를 제대로 변경하지 않으면 반복문이 끝나지 않을 수 있다.

예시:

```java
int count = 0;

while (count < 3) {
    count++;
    System.out.println(count);
}
```

- `count`는 반복 횟수를 제어하는 변수이다.
- `count++`가 실행될 때마다 값이 1씩 증가한다.
- `count`가 3이 되면 `count < 3`이 false가 되어 반복이 종료된다.

---

## 9. 반복 조건을 잘못 작성한 경우

```java
int count = 0;

while (count < 3) {
    System.out.println(count);
}
```

- 위 코드는 `count` 값이 변하지 않는다.
- 처음에 `count = 0`이다.
- `count < 3`은 계속 `true`이다.
- 조건이 계속 true이기 때문에 반복문이 끝나지 않는다.
- 이런 반복을 무한 반복이라고 한다.

정리:

```text
반복 조건에 사용되는 값이 변하지 않음
→ 조건이 계속 true
→ 반복문이 끝나지 않음
```

---

## 10. 무한 반복

```java
while (true) {
    System.out.println("무한 반복");
}
```

- 조건식이 항상 `true`이면 반복문은 끝나지 않는다.
- 일부러 무한 반복을 만들 수도 있지만, 종료 조건이 없으면 프로그램이 계속 실행된다.
- 무한 반복을 사용할 때는 보통 `break`를 함께 사용해서 특정 조건에서 빠져나오게 만든다.

---

## 11. do-while문

```java
do {
    실행할 코드
} while (조건식);
```

- `do-while`문은 먼저 코드를 한 번 실행한 뒤 조건식을 검사한다.
- 조건식이 `true`이면 다시 반복한다.
- 조건식이 `false`이면 반복을 종료한다.
- `while`문과 다르게 조건이 처음부터 false여도 최소 한 번은 실행된다.

---

## 12. do-while문 예제

```java
package loop;

public class DoWhile1 {
    public static void main(String[] args) {
        int i = 10;

        do {
            System.out.println("현재 숫자: " + i);
            i++;
        } while (i < 3);
    }
}
```

실행 결과:

```text
현재 숫자: 10
```

풀이:

```text
i = 10

do 블록 먼저 실행
현재 숫자: 10 출력
i++ → i = 11

조건 검사
i < 3 → 11 < 3 → false

반복 종료
```

- 조건은 처음부터 false이다.
- 하지만 `do-while`문은 조건을 나중에 검사한다.
- 그래서 코드가 최소 한 번은 실행된다.

---

## 13. while문과 do-while문의 차이

### 13-1. while문

```java
while (조건식) {
    실행할 코드
}
```

- 조건을 먼저 검사한다.
- 조건이 true이면 실행한다.
- 조건이 처음부터 false이면 한 번도 실행하지 않는다.

---

### 13-2. do-while문

```java
do {
    실행할 코드
} while (조건식);
```

- 코드를 먼저 실행한다.
- 실행 후 조건을 검사한다.
- 조건이 처음부터 false여도 최소 한 번은 실행한다.

정리:

```text
while
→ 조건 먼저 검사
→ false이면 실행 안 함

do-while
→ 코드 먼저 실행
→ false여도 최소 한 번 실행
```

---

## 14. break

- `break`는 반복문을 즉시 종료할 때 사용한다.
- 반복문 안에서 `break`를 만나면 반복 조건이 true여도 반복문을 빠져나간다.
- 보통 무한 반복 안에서 특정 조건을 만족하면 종료할 때 사용한다.
- `while`, `do-while`, `for`, `switch`에서 사용할 수 있다.

---

## 15. break 예제

```java
package loop;

public class Break1 {
    public static void main(String[] args) {
        int sum = 0;
        int i = 1;

        while (true) {
            sum += i;

            if (sum > 10) {
                System.out.println("합이 10보다 커짐: " + sum);
                break;
            }

            i++;
        }
    }
}
```

실행 결과:

```text
합이 10보다 커짐: 15
```

풀이:

```text
sum = 0, i = 1

sum += 1 → sum = 1
sum > 10 → false
i++ → i = 2

sum += 2 → sum = 3
sum > 10 → false
i++ → i = 3

sum += 3 → sum = 6
sum > 10 → false
i++ → i = 4

sum += 4 → sum = 10
sum > 10 → false
i++ → i = 5

sum += 5 → sum = 15
sum > 10 → true
출력 후 break 실행
반복문 종료
```

---

## 16. break 실행 흐름

- 반복문 실행 중 `break`를 만난다.
- 즉시 반복문을 종료한다.
- 반복문 아래 코드로 이동한다.
- 조건식이 아직 true여도 반복을 계속하지 않는다.

정리:

```text
break
→ 반복문 즉시 종료
→ 반복문 밖으로 이동
```

---

## 17. continue

- `continue`는 현재 반복만 건너뛰고 다음 반복으로 넘어갈 때 사용한다.
- 반복문 자체를 종료하지 않는다.
- `continue` 아래에 있는 코드는 실행하지 않는다.
- 다음 반복 조건 검사로 이동한다.

---

## 18. continue 예제

```java
package loop;

public class Continue1 {
    public static void main(String[] args) {
        int i = 1;

        while (i <= 5) {
            if (i == 3) {
                i++;
                continue;
            }

            System.out.println(i);
            i++;
        }
    }
}
```

실행 결과:

```text
1
2
4
5
```

풀이:

```text
i = 1
i == 3 → false
1 출력
i++ → i = 2

i = 2
i == 3 → false
2 출력
i++ → i = 3

i = 3
i == 3 → true
i++ → i = 4
continue 실행
아래 출력문 건너뜀

i = 4
i == 3 → false
4 출력
i++ → i = 5

i = 5
i == 3 → false
5 출력
i++ → i = 6

i <= 5 → false
반복 종료
```

- `i == 3`일 때 `continue`가 실행된다.
- 그래서 `3`은 출력되지 않는다.
- 반복문은 종료되지 않고 다음 반복으로 넘어간다.

---

## 19. continue 실행 흐름

- 반복문 실행 중 `continue`를 만난다.
- 현재 반복의 남은 코드를 건너뛴다.
- 반복문 처음으로 돌아간다.
- 조건식을 다시 검사한다.
- 조건이 true이면 다음 반복을 실행한다.

정리:

```text
continue
→ 현재 반복만 건너뜀
→ 반복문 처음으로 이동
→ 다음 반복 진행
```

---

## 20. break와 continue 차이

```text
break
→ 반복문 전체 종료
→ 반복문 밖으로 나감

continue
→ 현재 반복만 건너뜀
→ 반복문은 계속 진행
```

예시 비교:

```java
if (i == 3) {
    break;
}
```

- `i`가 3이면 반복문 자체를 끝낸다.

```java
if (i == 3) {
    continue;
}
```

- `i`가 3이면 현재 반복만 건너뛰고 다음 반복으로 넘어간다.

---

## 21. break와 continue를 사용할 때 주의할 점

- `break`는 반복문을 완전히 끝낸다.
- `continue`는 반복문을 끝내지 않는다.
- `continue`를 사용할 때 반복 조건에 사용되는 변수를 증가시키지 않으면 무한 반복이 발생할 수 있다.
- 특히 `while`문에서 `continue`를 사용할 때는 변수 증가 위치를 조심해야 한다.

잘못된 예시:

```java
int i = 1;

while (i <= 5) {
    if (i == 3) {
        continue;
    }

    System.out.println(i);
    i++;
}
```

- `i == 3`이 되면 `continue`가 실행된다.
- 그런데 `i++`가 실행되지 않는다.
- `i`는 계속 3이다.
- 조건 `i <= 5`는 계속 true이다.
- 그래서 무한 반복이 발생한다.

수정 예시:

```java
int i = 1;

while (i <= 5) {
    if (i == 3) {
        i++;
        continue;
    }

    System.out.println(i);
    i++;
}
```

- `continue` 전에 `i++`를 실행한다.
- 그래서 `i`가 4가 되고 다음 반복으로 넘어간다.
- 무한 반복을 피할 수 있다.

---

## 22. 오늘 작성한 예제 코드

```java
package loop;

public class LoopBreakContinuePractice {
    public static void main(String[] args) {
        int count = 0;

        while (count < 3) {
            count++;
            System.out.println("반복 횟수: " + count);
        }

        int i = 1;

        while (i <= 5) {
            if (i == 3) {
                i++;
                continue;
            }

            System.out.println("출력 숫자: " + i);
            i++;
        }

        int sum = 0;
        int num = 1;

        while (true) {
            sum += num;

            if (sum > 10) {
                System.out.println("합계가 10보다 커짐: " + sum);
                break;
            }

            num++;
        }
    }
}
```

실행 결과:

```text
반복 횟수: 1
반복 횟수: 2
반복 횟수: 3
출력 숫자: 1
출력 숫자: 2
출력 숫자: 4
출력 숫자: 5
합계가 10보다 커짐: 15
```

---

## 23. 오늘 새로 알게 된 점

- 반복문은 같은 코드를 여러 번 실행할 때 사용한다.
- `while`문은 조건이 true인 동안 반복한다.
- `while`문은 조건을 먼저 검사한다.
- 조건이 처음부터 false이면 `while`문은 한 번도 실행되지 않는다.
- `do-while`문은 코드를 먼저 실행하고 조건을 검사한다.
- `do-while`문은 조건이 처음부터 false여도 최소 한 번은 실행된다.
- 반복 조건에 사용되는 변수를 제대로 변경하지 않으면 무한 반복이 발생할 수 있다.
- `break`는 반복문을 즉시 종료한다.
- `continue`는 현재 반복만 건너뛰고 다음 반복으로 넘어간다.
- `break`와 `continue`는 반복 흐름을 제어할 때 사용한다.

---

## 24. 헷갈린 부분

- `while`문은 조건을 먼저 검사하고, `do-while`문은 먼저 실행한다는 차이가 헷갈릴 수 있다.
- `break`는 반복문 전체를 끝내고, `continue`는 현재 반복만 건너뛴다는 차이를 구분해야 한다.
- `continue`를 사용할 때 증가식을 빼먹으면 무한 반복이 생길 수 있다.
- `while (true)`는 의도적으로 무한 반복을 만들 때 사용하지만, 종료 조건과 `break`가 필요하다.
- 반복문에서는 조건식과 변수 변화가 같이 맞아야 정상적으로 종료된다.

---

## 25. 내 프로젝트와 연결한 부분

- 패션 추천 시스템에서 여러 옷 정보를 반복해서 검사할 때 반복문을 사용할 수 있다.
- 여러 코디 후보를 차례대로 분석할 때 `while`문을 사용할 수 있다.
- 특정 조건을 만족하면 분석을 중단할 때 `break`를 사용할 수 있다.
- 특정 옷 정보가 비어 있거나 분석 대상이 아니면 `continue`로 건너뛸 수 있다.
- 나중에 배열을 배우면 반복문으로 여러 옷 데이터를 순서대로 처리할 수 있다.

예시:

```java
int outfitCount = 0;

while (outfitCount < 3) {
    outfitCount++;
    System.out.println(outfitCount + "번째 코디 분석");
}
```

정리:

```text
outfitCount
→ 분석한 코디 개수

while (outfitCount < 3)
→ 코디를 3번 분석할 때까지 반복

outfitCount++
→ 반복할 때마다 분석 개수 증가
```

---

## 26. 패션 추천 시스템 예시 코드

```java
package loop;

public class FashionLoopPractice {
    public static void main(String[] args) {
        int outfitCount = 0;

        while (outfitCount < 3) {
            outfitCount++;
            System.out.println(outfitCount + "번째 코디 분석");
        }

        int score = 0;
        int addScore = 1;

        while (true) {
            score += addScore;

            if (score >= 5) {
                System.out.println("기준 점수 도달: " + score);
                break;
            }
        }
    }
}
```

실행 결과:

```text
1번째 코디 분석
2번째 코디 분석
3번째 코디 분석
기준 점수 도달: 5
```

---

## 27. 오늘의 핵심 정리

- 반복문은 같은 코드를 여러 번 실행할 때 사용한다.
- `while`문은 조건이 true인 동안 반복한다.
- `while`문은 조건을 먼저 검사한다.
- `do-while`문은 코드를 먼저 실행하고 조건을 검사한다.
- `do-while`문은 최소 한 번은 실행된다.
- 반복문에서는 조건식과 변수 변화가 중요하다.
- 조건이 계속 true이면 무한 반복이 발생할 수 있다.
- `break`는 반복문을 즉시 종료한다.
- `continue`는 현재 반복만 건너뛰고 다음 반복으로 넘어간다.
- `break`와 `continue`를 사용하면 반복 흐름을 제어할 수 있다.
- 오늘은 반복문 시작부터 `break`, `continue`까지 공부했다.

---

## 28. 다음에 할 일

- `for`문 공부하기
- `while`문과 `for`문의 차이 이해하기
- 중첩 반복문 공부하기
- 반복문 문제 풀이 정리하기
- 패션 추천 시스템에서 여러 코디 데이터를 반복 처리하는 코드 작성하기