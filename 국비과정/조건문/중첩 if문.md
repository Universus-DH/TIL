# 중첩 if문
**if문의 블럭**내에 **또 다른 if문**을 **포함**시키는 것이 가능한데 **이것을 중첩 if문**이라고 부르며 중첩의 횟수에는 거의 제한이 없다.
```java
     if (조건식1) {
        // 조건식1의 연산결과가 true일 때 수행될 문장들을 적는다.
           if (조건식2) {
             // 조건식1과 조건식2가 모두 true일 때 수행될 문장들 
           } else {
             // 조건식1이 true이고, 조건식2가 false일 때 수행되는 문장들 
           }
   } else {
        // 조건식1이 false일때 수행되는 문장들
   }
```
* 위와 같이 **내부의 if문은 외부의 if문**보다 **안쪽으로 들여쓰기**를 해서 **두 if문의 범위가 명확히 구분**될수 있도록 작성해야한다. <br>
* **중첩 if문에서는 괄호{}의 생략**에 **더욱 조심**해야 한다. **바깥쪽의 if문**과 **안쪽의 if문**이 **서로 엉켜서** if문과 else블럭의 관계가 의도한 바와 다르게 형성될 수도 있기 때문이다.

---

## **중첩 if문** 예제
```java
import java.util.Scanner;

public class OverlapIf {
	public static void main(String [] args) {   

		int score = 0;
		char grade = ' ', opt = ' ';
		
		System.out.print("점수를 입력하세요.>");
		
		Scanner scanner = new Scanner(System.in);
		score = scanner.nextInt(); // 화면을 통해 입력받은 점수를 score에 저장
		
		System.out.printf("당신의 점수는 %d입니다.%n", score);
		
		if (score >= 90) {           // score가 90보다 같거나 크면 A학점(grade)
			grade = 'A';
			if ( score >= 98) {      // 90점 이상 중에서도 98점 이상은 A+
				opt = '+';
			} else if (score < 94) { // 90점 이상 94점 미만 A-
				opt = '-';
			}
			
		} else if (score >= 80) {    // score가 80점 보다 같거나 크면 B학점(grade)
			grade = 'B'; 
			if (score >= 88) {
				opt = '+';
		    } else if (score < 84) {
				opt = '-';
		    }
			
		} else {                     // 나머지는 C학점(gared)
			grade = 'C';
		}		
        System.out.printf("당신의 학점은 %c%c입니다.%n", grade, opt);
	}
} 
```
* **결과1** 점수를 입력해주세요.> **81**
  *      당신의 점수는 81입니다. 
         당신의 학점은 B-입니다.
* **결과2** 점수를 입력해주세요.> **85**
  *      당신의 점수는 85입니다. 
         당신의 학점은 B입니다.
위 예제는 모두 **3개의 if문**으로 이루어져 있으며 **if문 안에 또 다른 2개의 if문**을 포함하고 는 모습을 하고있다. <br>
**제일 바깥쪽에 있는 if문**에서 점수에 따라 학점(grade)을 결정하고,**내부 if문** 에서는 학점을 더 세부적으로 나누어서 평가를 하고 그 결과를 출력한다.<br>
 **외부 if문**의 조건식에 의해 한번 걸러졌기 때문에 **내부 if문**의 조건식은 더 간단해 질 수 있다.
