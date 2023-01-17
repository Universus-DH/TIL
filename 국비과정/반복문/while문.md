# while문 
for문에 비해 while문은 구조가 간단하다. if문처럼 조건식과 블럭{}만으로 이루어져 있다.<br>
다만 if문과 달리 **while문은 조건식이 '참(true)인 동안'**, 즉 **조건식이 거짓이 될때까지 블럭{} 내의 문장을 반복**한다.
```java
     while (조건식) {
        // 조건식의 연산결과가 참(true)인 동안, 반복될 문장들을 적는다.
     }
```
while문은 먼저 조건식을 평가해서 조건식이 거짓이면 문장 전체를 벗어나고, 참이면 블럭{}내의 문장을 수행하고 다시 조건식으로 돌아간다.  <br>
**조건식이 거짓**이 될 때까지 이 과정이 **계속 반복**된다.

---

## for문과 while문의 비교

**for문**
```java
// 초기화, 조건식, 증감식
     for(int i=1; i<=10; i++)  {
        System.out.println(i);
     }
```

* 1부터 10까지 정수를 순서대로 출력하는 **for문을 while문**으로 **변경**하면 아래와 같다.

```java
     int i=1; // 초기화
     
     while(i<=10) { // 조건식
         System.out.println(i); 
         i++;       // 증감식
     }
```
위의 두 코드는 완전히 동일하다. **for문은 초기화, 조건식, 증감식**을 **한 곳**에 모아 놓은 것일뿐 while문과 다르지않다.<br>
그래서 for문과 while문은 항상 서로 변환이 가능하다.
그래도 이 경우 while문 보다 for문이 더 간결하고 알아보기 쉽다.<br>
**만일 초기화이나 증감식**이 **필요하지 않는** 경우라면, **while문이 더 적합**하다.

## while문 예제1

```java
	public static void main(String [] args) {   
		int i = 5;
		
		while(i--!=0) {
			System.out.println(i + " - I can do it.");
		}
	}
} 
/* 
출력 값
4 - I can do it.
3 - I can do it.
2 - I can do it.
1 - I can do it.
0 - I can do it.
*/
```
변수 i의 값만큼 블럭{}을 반복하는 예제이다. i의 값이 5이므로 'I can do it.'이 모두 5번(4~0)출력되었다<br>
**while문의 조건식 'i--!=0'**는 **i의 값이 0이 아닌 동안만 참**이 되고, **i의 값이 매 반복마다 1씩 감소**하다 **0이 되면 조건식이 거짓**이 되어 **while문을 벗어난다.**

---

* 다음은 1부터 몇까지 더해야 100을 넘지 않는지 알아내는 예제이다.
```java
	public static void main(String[] args) {
		int sum = 0;
		int i = 0;
		// i를 1씩 증가시켜서 sum에 계속 더해간다.
		while (sum <= 100) {
			System.out.printf("%d - %d%n", i, sum);
			sum += ++i;
		}
	}
}
/*
출력 값
0 - 0
1 - 1
2 - 3
(...)
11 - 66
12 - 78
13 - 91
*/
```
## while문 예제2
```java
import java.util.Scanner;

	public static void main(String[] args) {
		int num = 0, sum = 0;
		System.out.print("숫자를 입력하세요.(예:12345)>");

		Scanner scanner = new Scanner(System.in);
		String tmp = scanner.nextLine(); // 화면을 통해 입력받은 내용을 tmp에 저장
		num = Integer.parseInt(tmp); // 입력받은 문자열(tmp)을 숫자로 변환

		while (num != 0) {
			// num을 10으로 나눈 나머지를 sum에 더함
			sum += num % 10; // sum = sum + num%10;
			System.out.printf("sum=%d num=%d%n", sum, num);

			num /= 10; // num = num / 10; num을 10으로 나눈 값을 다시 num에 저장
		}
		System.out.println("각 자리수의 합:" + sum);
	}
}
```
사용자로부터 숫자를 입력받고, 이 숫자의 각 자리의 합을 구하는 예제이다. <br> 실행 결과에서 알 수 있듯이 12345를 입력하면, 결과는 15(1+2+3+4+5)이다.<br> 어떤 수를 10으로 나머지 연산하면 마지막 자리를 얻을 수 있다.
그리고 10으로 나누면 마지막 한자리가 제거된다.
<br>
그래서 입력 받은 숫자 num을 0이 될 때까지 반복해서 10으로 나눠가면서, 10으로 나머지 연산을 하면 num의 모든 자리를 얻을 수 있다.

|  num  | num%10 | sum = sum + num%10 <br> (sum+=num%10) | num = num / 10 <br> (num/=10) |
| :---: | :----: | :-----------------------------------: | :---------------------------: |
| 12345 |   5    |               5 = 0 + 5               |       1234 = 12345 / 10       |
| 1234  |   4    |               9 = 6 + 4               |        123 = 1234 / 10        |
|  123  |   3    |              12 = 9 + 3               |         12 = 123 / 10         |
|  12   |   2    |              14 = 12 + 2              |          1 = 12 / 10          |
|   1   |   1    |              15 = 14 + 1              |          0 = 1 / 10           |
|   0   |   -    |                   -                   |               -               |

num의 값은 'num/=10'에 의해 한자리씩 줄어들다가 0이 되면, while문의 조건식이 거짓이 되어 반복을 멈춘다.
