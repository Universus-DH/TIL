# if-else문
**if**문의 변형인 **if-else**문의 구조는 다음과 같다. **if문에 'else블럭'** 이 더 추가되었다.<br>
**'else'의 뜻**이 '그 밖의 다른'이므로 조건식의 결과가 참이 아닐 때, 즉 거짓일 때 **else블럭**의 문장을 수행하라는 뜻이다.
```java
    if (조건식) {
        // 조건식이 true일 때 수행될 문장들을 적는다.
    }else {
        // 조건식이 false일 때 수행될 문장들을 적는다.
    }
```
조건식의 결과에 따라 이 두 개의 블럭{}중 어느 한 블럭{}의 내용이 수행되고, 전체 if문을 벗어나게 된다.
<br>
두 블럭{}의 내용이 모두 수행되거나, 모두 수행되지 않는 경우는 있을 수 없다.
<br>

* **if문**
```java
int input = 0;

     if(input == 0 ) {
        System.out.println("0입니다.");             
     }

     if(input != 0 ) {
        System.out.println("0이 아닙니다.");
     }
   }
} 
```
* **if-else문**
```java
int input = 0;

     if(input == 0 ) {
        System.out.println("0입니다.");             
     }else{
        System.out.println("0이 아닙니다.");
     }
   }
} 
```
**if문** 코드는 두 개의 조건식을 계산해야하지만,<br>
**if-else문**을 사용한 오른쪽의 코드는 하나의 조건식만 계산하면 되므로 더 효율적이고 간단하다.

---

* **예제**
```java
import java.util.Scanner; // Scanner class를 사용하기위해 Scanner - java.util 생성

public class Ifelse {
	public static void main(String [] args) {   


		System.out.print("숫자를 입력하세요.>");
		Scanner scanner = new Scanner(System.in);
		int input =  scanner.nextInt();  // 화면을 통해 입력받은 숫자를 intput에 저장
		
		if(input == 0 ) {    // input 0인 경우
			System.out.println("입력하신 숫자는 0입니다.");
		}else {              // input 0이 아닌경우
			System.out.println("입력하신 숫자는 0이 아닙니다.");
		}	
    }  // main의 끝
} 
```
* **결과1** : 숫자를 하나만 입력하세요.> **5** 
  * 입력하신 숫자는 0이 아닙니다.
* **결과2** : 숫자를 하나만 입력하세요.> **0**
  * 입력하신 숫자는 0입니다.
