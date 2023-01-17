# break문

반복문에서도 break문을 사용할 수 있는데, switch문에서 그랬던 것 처럼, break문은 자식이 포함된 가장 가까운 반복문을 벗어난다.<br>
주로 if문과 함께 사용되어 특정 조건을 만족할 때 반복문을 벗어나게 한다.

```java
	public static void main(String[] args) {
		int sum = 0;
		int i = 0;

		while (true) {
			if (sum > 100)
				break;
			++i;
			sum += i;
		} // end of while

		System.out.println("i=" + i);
		System.out.println("sum=" + sum);
	}
}
/*
출력 값
i=14
sum=105
*/
```
숫자를 1부터 계속 더해 나가서 몇까지 더하면 합이 100을 넘는지 알아내는 예제이다. <br>
**i의 값을 1부터 1씩 계속 증가**시켜가며, 더해서 **sum에 저장**한다. **sum의 값이 100을 넘으면** if문의 조건식이 참이므로 **break문이 수행**되어 자신이 속한 반복문을 즉시 벗어난다.

* 이처럼 무한 반복문에는 조건문과 break문이 항상 같이 사용된다. 
   * 그렇지 않으면 무한히 반복되기 때문에 프로그램이 종료되지 않는다.

**sum += i;와 ++i; 두 문장을 
sum += ++;과 같이 한 문장으로 쓸 수 있다.**

---

# continue문 
continue문은 반복문 내에서만 사용될 수 있으며, 반복이 진행되는 도중에 continue문을 만나면 반복문의 끝으로 이동하여 다음 반복으로 넘어간다. <br>
for문의 경우 증감식으로 이동하며, while문과 do-while문의 경우 조건식으로 이동한다.

<br>

**continue문**은 **반복문 전체를 벗어나지 않고 다음 반복을 계속 수행**한다는 점이 break문과 다르다. <br>
주로 if문과 함께 사용되어 특정 조건을 만족하는 경우에 continue 이후의 문장들을 수행하지 않고 다음 반복으로 넘어가서 계속 진행하도록 한다.<br>
 전체 반복 중에 특정조건을 만족하는 경우를 제외하고자 할 때 유용하다.
```java
	public static void main(String[] args) {
		for (int i = 0; i <= 10; i++) {
			if (i % 3 == 0)
				continue;
			System.out.println(i);
		}
	}
}
/*
1
2
4
5
7
8
10
*/
```
1과 10사이의 숫자를 출력하되 그 중에서 3의 배수인 것은 제외하도록 하였다. <br>
i의 값이 3의 배수인 경우, if문의 조건식 'i%3==0'은 참이 되어 continue문에 의해 반복문의 블럭 끝'}'으로 이동한다. <br>
즉, **continue문과 반복문 블럭의 끝 '}' 사이**의 **문장들을 건너뛰고 반복을 이어 가는 것**이다.

---

# break문과 continue문 예제

```java
	public static void main(String[] args) {
		int menu = 0;
		int num = 0;

		Scanner scanner = new Scanner(System.in);

		while (true) {
			System.out.println("(1) square");
			System.out.println("(2) square root");
			System.out.println("(3) iog");
			System.out.println("원하는 메뉴(1~3)를 선택하세요.(종료:0)>");

			String tmp = scanner.nextLine();  // 화면에서 입력받은 내용을 tmp에 저장
			menu = Integer.parseInt(tmp);     // 입력받은 문자열(tmp)을 숫자로 변환

			if (menu == 0) {
				System.out.println("프로그램을 종료합니다.");
				break;
			} else if (!(1 <= menu && menu <= 3)) {
				System.out.println("메뉴를 잘못 선택하셨습니다.(종료는 0)");
				continue;
			}

			System.out.println("선택하신 메뉴는 " + menu + "번입니다.");
		}
	}
}
```
*     (1) square
      (2) square root
      (3) iog
      원하는 메뉴(1~3)를 선택하세요.(종료:0)> 4
      메뉴를 잘못 선택하셨습니다.(종료는 0)

      (1) square
      (2) square root
      (3) iog
      원하는 메뉴(1~3)를 선택하세요.(종료:0)> 1
      선택하신 메뉴는 1번입니다.

      (1) square
      (2) square root
      (3) iog
      원하는 메뉴(1~3)를 선택하세요.(종료:0)>
      0
      프로그램을 종료합니다.
메뉴를 보여주고 선택하게 하는 예제이다. 메뉴를 잘못 선택한 경우, continue문으로 다시 메뉴를 보여주고, 종료(0)를 선택한 경우 break문으로 반복을 벗어나 프로그램이 종료되도록 했다.
