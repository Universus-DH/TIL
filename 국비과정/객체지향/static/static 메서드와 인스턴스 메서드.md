# static 메서드와 인스턴스 메서드

변수에서 그랬던 것과 같이, 메서드 앞에 static이 붙어 있으면 클래스메서드이고, 붙어있지않으면 인스턴스 메서드이다.
<br>
클래스 메서드도 클래스변수처럼, 객체를 생성하지 않고도 '클래스이름.메서드이름(매개변수)'와 같은 식으로 호출이 가능하다. 
**반면에 인스턴스 메서드는 반드시 객체를 생성해야하만 호출 할수있다.**

그렇다면 클래스를 정의할 때, 어느 경우에 static을 사용해서 클래스 메서드로 정의해야하는 것일까?

클래스는 '**데이터(변수)와 데이터에 관련된 메서드의 집합**'이므로, 같은 클래스 내에 있는 메서드와 멤버변수는 아주 밀접한 관계가 있다.
**인스턴스 메서드**는 인스턴스 변수와 관련된 작업을 하는, 즉 메서드의 작업을 수행하는데 인스턴스 변수를 필요로로 하는 메서드이다.
그런데 인스턴스 변수는 인스턴스(객체)를 생성해야만 호출할 수 있는 것이다.
반면에 메서드 중에서 인스턴스와 관계없는(인스턴스 변수나 인스턴스 메서드를 사용하지않는)
메서드를 클래스 메서드(static메서드)로 정의한다.

---

## 멤버변수 통칭

* **멤버변수** : 클래스 영역에 선언된 변수
* **클래스변수** : static이 붙은 변수
* **인스턴스변수** : static이 붙어있지 않은 변수 

---

# static 메서드와 인스턴스 메서드

```java
public class MyMath2 {
	long a, b;
	
	// 인스턴스 변수a, b만을 이용해서 작업하므로 매개변수가 필요없다.
	long add()	    { return a + b; }
	long subtract() { return a - b; }
	long multiply() { return a * b; }
	double divide() { return a / b; }
	
	// 인스턴스 변수와 관계없이 매개변수만으로 작업이 가능하다.
	static long  add(long a,long b)        { return a + b; }
	static long  subtract(long a, long b)  { return a - b; }
	static long  multiply(long a, long b)  { return a - b; }
	static double divide(long a, long b)   { return a / b; }
}
```
```java
public class Ex6_9 {
	public static void main(String[] args) {
		// 클래스 메서드 호출, 인스턴스 생성없이 호출가능
		System.out.println(MyMath2.add(200L, 100L));
		System.out.println(MyMath2.subtract(200L, 100L));
		System.out.println(MyMath2.multiply(200L, 100L));
		System.out.println(MyMath2.divide(200L, 100L));
		
		MyMath2 mm = new MyMath2(); // 인스턴스 생성
		mm.a = 200L;
		mm.b = 100L;
		// 인스턴스 메서드는 객체 생성후에만 호출이 가능함.
		System.out.println(mm.add());
		System.out.println(mm.subtract());
		System.out.println(mm.multiply());
		System.out.println(mm.divide());
	}
}
/*
300
100
20000
2.0
300
100
20000
2.0
*/
```

인스턴스 메서드인 add(), subtract(), multiply(), divide()는 인스턴스변수인 a와 b만으로도 충분히 작업이 가능하기 때문에, 매개변수를 필요로 하지 않으므로 괄호()에 매개변수를 선언하지 않았다.
<br>
반면에 add(long a, long b), subtract(long a, long b)등은 인스턴스 변수없이 매개변수 만으로 수행하기 때문에 static을 붙여서 클래스메서드로 선언하였다.
<br>
그래서 main메서드에서 보면, 클래스메서드는 객체생성없이 바로 호출이 가능했고,
인스턴스 메서드는 MyMath2클래스의 객체 인스턴스를 생성한 후에야 호출이 가능했다.
