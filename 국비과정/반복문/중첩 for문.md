# 중첩 for문
for문 안에 또 다른 for문을 포함시키는 것이 가능하며, 중첩 for문이라고 한다.<br>
중첩 횟수는 거의 제한이없다. 중첩 for문을 설명하는데 별찍기 만큼 좋은 것은 없다.
* 만일 다음과 같이 5행 10열의 별'*'을 찍으려면 어떻게 해야 할까?
```
    **********
    **********
    **********
    **********
    **********
```

가장 간단한 방법은 다음과 같이 한 줄씩 5번 출력 하는 것이다.
```java
    System.out.println("**********");
    System.out.println("**********");
    System.out.println("**********");
    System.out.println("**********");
    System.out.println("**********");
```

그러나 우리는 **for문**을 배웠으니, 다음과 같이 간단히 할수 있다.
```java
    for(int i=1; i<=5; i++) {
         System.out.println("**********");   
    }
```

'System.out.println("**********");' 역시 반복적인 일을 하는 문장이니 for문으로 바꿀 수 있다. 이 문장을 for문으로 바꾸면 다음과 같다.
  
*     System.out.println("**********");
              
    ↓                 
*     for(int j=1; j<=10; j++) { 
          System.out.println("**********");
      }    
---      
첫번째 아래의 문장 대신 두번째 아래의 fof문을 이전의 for문에 넣으면 다음과 같이 **두 개의 for문이 중첩**된 형태가 된다.
*     for(int i=1; i<=5; i++)  {
         System.out.println("**********")
      }
    ↓
*       for(int i=1; i<=5; i++) {
			for(int j=1; j<=10; j++) {
			System.out.print("*");
	  }
---

이번엔 다음과 같은 삼각형 모양의 별을 출력해보자.
```
   *
   **
   ***
   ****
   *****
```
앞서 배운 바와 같이 가로로 출력하려면, println메서드 대신 print메서드로 출력하면 된다.
아래의 for문은 '*****'을 출력하고 줄 바꿈을 한다.

---

```java
		for (int j = 1; j <= 5; j++) {
			System.out.print("*");      // ***** 출력
		}
		System.out.println();           // 줄 바꿈을 한다.

//따라서 다음과 같이 코드를 작성하면, 우리가 원하는 결과를 얻을 수 있다.

		for(int j=1;j<=1;j++) {System.out.print("*");} System.out.println(); //*
		for(int j=1;j<=2;j++) {System.out.print("*");} System.out.println(); //**
		for(int j=1;j<=3;j++) {System.out.print("*");} System.out.println(); //***
		for(int j=1;j<=4;j++) {System.out.print("*");} System.out.println(); //****
		for(int j=1;j<=5;j++) {System.out.print("*");} System.out.println(); //*****
	}
}
```
위 문장들을 잘 보면 조건식의 숫자만 변할 뿐 나머지는 같다. 똑같은 내용이 반복되는데. <br>
반복문으로 간단히 처리할 방법이 없을까? <br>
이럴 때는 한 문장의 조건식에 숫자 대신 변수를 i를 넣고, **이 문장을 i의 값이 1부터 5까지 증가하는 for문 안에 넣으면 된다.**
```java
	public static void main(String[] args) {

		for(int i=1; i<=5; i++) {
		   for(int j=1; j<=i; j++) {
			System.out.print("*");
		}
		System.out.println();
		}
	}
}
// *
// **
// ***
// ****
// *****
```
