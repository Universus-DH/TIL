# return문 

`return문`은 현재 실행중인 메서드를 종료하고 호출한 메서드로 되돌아간다. 지금까지 반환값이 있을 때만 return문을 썼지만, 원래는 반환값의 유무에 관계없이 모든 메서드에는 적어도 하나의 return문이 있어야 한다. 그런데도 반환타입이 void인 경우, return문 없어도 아무런 문제가 없었던 이유는 **컴파일러가 메서드의 마지막에 'return;'을 자동적으로 추가해주었기 때문이다.**
```java
     void printGugudan(int dan) {
          for(int i=1; i<=9; i++) {
            System.out.printf("%d * %d = %d%n", dan, i, dan * i );
          }
//        return;  // 반환 타입이 void이므로 생략가능. 컴파일러가 자동추가
     }
```

---

그러나 **반환타입이 void가 아닌 경우**, 즉 반환값이 있는 경우, **반드시 return문이 있어야 한다.** return문이 없으면 컴파일 에러(error: missing return statement)가 발생한다.
```java
     int multiply(int x, int y) {
        int result = x * y;

        return result;        // 반환 타입이 void가 아니므로 생략불가
     }
```
---

아래의 코드는 두 값 중에서 큰 값을 반환하는 메서드이다. 이 메서드의 리턴타입이 int이고,<br>
int타입의 값을 반환하는 return문이 있지만, return문이 없다는 에러가 발생한다.<br>
왜냐하면 if**문 조건식의 결과에 따라 return문이 실행되지 않을 수도 있기 때문이다.**
```java
     int max(int a, int b) {
          if(a > b)
             return a;    // 조건식이 참일 때만 실행된다.
     }
```
---

그래서 이런 경우 다음과 같이 **if문의 else블럭**에 **return문을 추가해서, 항상 결과값**이 **반환**되도록 해야 한다.
```java
     int max(int a, int b) {
          if(a > b)
               return a;  // 조건식이 참일 때 실행된다.
          else
               return b;  // 조건식이 거짓일 때 실행된다.
     }
```
