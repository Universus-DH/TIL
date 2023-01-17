# do - whlie문
do - while문은 while문의 변형으로 기본적인 구조는 while문과 같으나 조건식과 블럭{}의 순서를 바꿔놓은 것이다. 그래서 while문과 반대로 블럭{}을 수행한 후에 조건식을 평가한다.<br>
**while문은 조건식**의 결과에 따라 블럭{}이 **한 번도 수행되지 않을 수** 있지만, **do-while문은 최소한 한번**은 **수행될 것**을 보장한다.

```java
     do {
        // 조건식의 연산결과가 참일 때 수행될 문장들을 적는다.(처음 한 번은 무조건 실행)
     } whlie (조건식); // ← 끝에 ; 을 잊지 않도록 주의
```
* 많이 쓰이지는 않지만, 다음의 예제처럼 반복적으로 사용자의 입력을 받아서 처리할 때 유용하다.

```java
import java.util.Scanner;

	public static void main(String[] args) {
		int input = 0, answer = 0;

		answer = (int) (Math.random() * 100) + 1; // 1~100 사이의 임의의 수를 저장.
		Scanner scanner = new Scanner(System.in);

		do {
			System.out.print("1과 100사이의 정수를 입력하세요.>");
			input = scanner.nextInt();

			if (input > answer) {
				System.out.println("더 작은 수로 다시 시도해보세요.");
			} else if (input < answer) {
				System.out.println("더 큰 수로 다시 시도해보세요.");
			}
		} while (input != answer);
		System.out.println("정답입니다.");
	}
}
/*
1과 100사이의 정수를 입력하세요.>70
더 작은 수로 다시 시도해보세요.
1과 100사이의 정수를 입력하세요.>60
더 작은 수로 다시 시도해보세요.
1과 100사이의 정수를 입력하세요.>50
더 큰 수로 다시 시도해보세요.
1과 100사이의 정수를 입력하세요.>55
더 작은 수로 다시 시도해보세요.
1과 100사이의 정수를 입력하세요.>54
정답입니다.
*/
```

* Math.random()을 이용해서 1과 100사이의 수를 변수 answer에 저장하고, 이 값을 맞출 때까지 반복하는 예제이다.<br>
  * 사용자 입력인 input이 변수 answer의 값과 다른동안 반복하다가 두 값이 같으면 반복을 벗어난다. 
