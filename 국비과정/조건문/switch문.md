# **switch문**
if문은 조건식의 결과가 **true참과 flase거짓**, 두 가지 밖에 없기 때문에. 경우의 수가 많아질수록 
<br>
**else-if**를 계속 추가해야 하므로 조건식이 많아져서 복잡해지고, 여러 개의 조건식을 계산해야 하므로 처리시간도 많이 걸린다. <br>

* **if문과 달리 switch문**은 **단 하나의 조건식**으로 많은 경우의 수를 처리 할수 있고, 표현도 간결하므로 알아보기 쉽다. <br>
 
* 그래서 처리할 경우의 수가 많은 경우에는 if문 보다 switch문으로 작성하는 것이 좋다.
다만 **switch문은 제약조건**이 있기 때문에,<br>
**"경우의 수가 많아도 어쩔 수 없이 if문으로 작성해야 하는 경우가 있다."**

---

**switch문은 조건식**을 먼저 계산한 다음, 그 결과와 일치하는 **case문으로** 이동한다.<br>
이동한 case문 아래에 있는 문장들을 수행하며, break문을 만나면 전체 switch문을 빠져나가게 된다.
1. 조건식을 계산한다.
2. 조건식의 결과와 일치하는 case문으로 이동한다.
3. 이후의 문장들을 수행한다,
4. break문이나 switch문의 끝을 만나면 switch문 전체 빠져간다.
```java
   switch (조건식) {
        case 값1 : 
              // 조건식의 결과가 값1과 같은 경우 수행될 문장들
              // ...
              break;
        case 값2 :
              // 조건식의 결과가 값2와 같을 경우 수행될 문장들 
              // ...
              break;    // switch문을 벗어난다.
        //...
        default : 
              // 조건식의 결과와 일치하는 case문이 없을 때 수행될 문장들 
              // ...                         
    }
```
* 만일 조건식의 결과와 일치하는 **case문**이 하나도 없는 경우에는 **default문**으로 이동한다.<br>
  * **dafault문**은 " if문의 else블럭과 같은 역할" 을 한다고 보면 이해가 쉽다.
  * **dafault문**의 위치는 어디라도 상관없으나 보통 " 마지막에 놓기 때문에 break문을 쓰지 않아도 된다. "

* **switch문**에서 **break문**은 " 각 case문의 영역을 구분" 하는 역할을 하는데,
  * 만일 break문을 생략하면 case문 사이의 구분이 없어지므로 다른 break문을 만나거나 switch문 블럭{}의 끝을 만날 때까지 나오는 모든 문장들을 수행한다. 
  * 이러한 이유로 각 case문의 마지막에 break문을 빼먹는 실수를 하지않도록 주의해야 한다.

---

# switch문의 **제약조건**

**switch문의 조건식**은 결과값이 **반드시 정수**이어야 하며,
이 값과 일치하는 case문으로 이동하기 때문에 **case문의 값 역시 정수**이어야 한다. <br>
그리고 중복되지 않아야 한다.같은 값의 case문이 여러 개이면, 어디로 이동해야할 지 알 수 없기 때문이다. <br>
 게다가 **case문의 값은 반드시 상수**이어야 한다. **변수나 실수는 case문의 값으로 사용할 수 없다.**

<br>

* **switch문의 제약조건**
  * switch문의 조건식 결과는 정수 또는 문자열이어야 한다.
  * case문의 값은 정수 상수(문자포함), 문자열만 가능하며, 중복되지 않아야한다.

## **case문**의 몇 가지 예
```java
	public static void main(String [] args) {   

		int num, result;
		final int ONE = 1;
		// ...
		switch(result) { 
		     case  '1' :             // OK. 문자 리터럴(정수 49와 동일)
		     case  ONE :             // OK. 정수 상수
		     case "YES":             // OK. 문자열 리터럴
		     case  num :             // Error. 변수는 불가
		     case  1.0 :	         // Error. 실수도 불가
        // ...     
		}
```
문자 '1' 은 정수 49와 동등하므로 문제가 없고, ONE은 정수가 아닌 것처럼 보이지만, 'final'이 붙은 정수 상수이므로 case문의 값으로 적합하다. <br>
그러나 변수나 실수 리터럴은 case문의 값으로 적합하지않다.

---

# **switch문의 제약조건** 예제

```java
import java.util.Scanner;

public class SwitchBreak {
	public static void main(String [] args) {   

		System.out.print("현재 월을 입력하세요.>");
		
		Scanner scanner = new Scanner(System.in);
		int month = scanner.nextInt();  // 화면을 통해 입력받은 숫자를 month에 저장
		
		switch(month) {
		   case 3:
		   case 4:
		   case 5:
			   System.out.println("현재의 계절은 봄입니다.");
			   break;
		   case 6: case 7: case 8:
			   System.out.println("현재의 계절은 여름입니다.");
			   break;
		   case 9: case 10: case 11: 
			   System.out.println("현재의 계절은 가을입니다.");
			   break;
		   default:
	//	   case 12: case 1: case 2:
			   System.out.println("현재의 계절은 겨울입니다.");			   	
		}
	}
} 
```
*  **결과** : 현재 월을 입력하세요.> **1**
   * **출력** : 현재의 계절은 겨울입니다.

**case문은 한 줄에 하나씩 쓰던, 한 줄에 붙여서 쓰던 상관없다.**

---

그리고 예제의 switch문을 if문으로 변경하면 다음과 같다.
```java    
     if(month==3 || month==4 || month==5) {
        System.out.println("현재의 계절은 봄입니다.");
     } 
     else  if(month==6 || month==7 || month==8) {
        System.out.println("현재의 계절은 여름입니다.");
     } 
     else  if(month==9 || month==10 || month==11) {
        System.out.println("현재의 계절은 가을입니다.");
     }   
     else { //(month==12 || month==1 || month==2) 
        System.out.println("현재의 계절은 여름입니다.");
     }
```     
