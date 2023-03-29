## 세부 목차
1. [제네릭의 이해](#21-1-제네릭의-이해)
2. [제네릭의 기본 문법](#21-2-제네릭의-기본-문법)


## 21-1 제네릭의 이해


### 제네릭 이전 코드
https://github.com/j-jh-Study/hotblood-java-programing/blob/d88ec0a8e752c54f51b210ac4c9bd138556b7610/javaCode/src/main/java/FruitAndBox2.java#L9-L10

" 인스턴스에서 내용물을 꺼낼 때 형 변환을 해야함"
https://github.com/j-jh-Study/hotblood-java-programing/blob/d88ec0a8e752c54f51b210ac4c9bd138556b7610/javaCode/src/main/java/FruitAndBox2.java#L30-L39

참조변수가 Object 형이기 때문에 저장 될때나 꺼낼때 실수 가 발생할 수 있다

하지만 문제점은 저장할 때나 꺼낼때 실수가 있다는점 .. 컴파일러가 잡아 주면 좋지만 이런 경우는 잡아 주기 힘들다
```java
System.out.println(abox.get())  
```

---
### 제네릭 기반 클래스 정의하기 

```java

class Box<T>{
 private T ob;
 public void set(T o){
  ob = 0;
 }
 
 pubic T get(){
   return ob;
 }
```

T는 인스턴스 생성 순간에 결정 !


용어정리
- 타입매개변수(Type Parameter) T 같은것들
- 타입 인자(Type Argument) T를 정의한 것.. Box<Apple> 에서 Apple
- 매개변수화 타입(Parameterized Type) Box<Apple>  == 제네릭타입 
 
 
## 21-2 제네릭의 기본 문법
 
### 다중 매개변수 기반 제레릭 클래스의 정의

```java
 <L,R> 처럼 여러개 선언 가능하다 ~
 ```

타입 매개변수의 이름은 짓기 나름 ~ 일반적으로 두가지 규칙을 지킨다
- 한 문자로 이름을 짓는다
- 대문자로


### 기본자료형에 대한 제한 그리고 래퍼 클래스

<> 안에는 기본자료형 안들어가고 대신 그의 래퍼 클래스가 들어감 
  ex) int -> Integer 
  
필요 상황에 따라 오토 박싱과 언박싱이 진행
  
### 타입인자의 생략
```java
  Box<Apple> aBox = new Box<Apple>();
  //이걸 밑에와 같이 쓸 수 있다 .. 컴파일러가 알아서 추론함
  
  Box<Apple> aBox = new Box<>();
  
```
  
### '매개변수화 타입'을 '타입 인자'로 전달하기
  
```java
  ...
  Box<Box<Box<String>>> zBox = new Box<>();
  ...
  // 요렇게 Box<T> 라고 정의한걸 여러번 재활용 가능하다 
  
```

### 제네릭 클래스의 타입 인자 제한하기
  
지금은 object와 유사한 느낌이다 뭐든 담을 수 있으니..
따라서 담고 싶은 걸 제한 할때 사용하는것이 extends! 상속되시것다 ! 

```java
  
  class Box<T extends Number>{...}
  
```
  -> 이렇게 되면 인스턴스 생성시 타입인자로 Number 또는 이를 상속한 클래스만 올 수 있다 .
  
장점 ! 
  어떤 클래스를 참조할건지 알 수 있기때문에 메소드 호출이 가능해진다 
  
```java
  
  class Box<T extends Number>{
    private T ob;
  ...
   public int toIntBalue(){
    return ob.intBalue();
 }
}
  
```
### 제네릭 클래스의 타입 인자를 인터페이스로 제한하기
  
  인터페이스로도 제한 가능하다 ..! 
  그러면 인터페이스 오버라이드해서 내 입맛에 알맞게 재정의해서 사용하는게 가능하다는 소리 ! 
  
  하나 이상의 클래스와 하나 이상의 인터페이스에 대해 동시에 제한을 할때는 & 를 이용해서 제한 하자
  
  ```java
  
  class Box<T extends Number & Eatable>{...  }
  
  ```
  
  ### 제네릭 메소드의 정의
  
  일부 메소드에 대해서만 제네릭으로 정의하는 것도 가능
  
  ```java
   public static <T> Box<T> makeBox(T o){...}
  ...
 
  제네릭 클래스는 인스턴스 생성 시 자료 형이 결정.. 반면 
  제네릭 메소드는 '메소드 호출시에 자료형이 결정'
  
  
  ```java
  Box<String> sBox = BoxFactory.<String>makeBox("Sweet");
  Box<Double> dBox = BoxFactory.<Double>makeBox(7.59);
  
  // 여기서 두번째 타입인자는 생략가능하다 
   Box<String> sBox = BoxFactory.makeBox("Sweet");
  Box<Double> dBox = BoxFactory.makeBox(7.59);
  ```
  
  반환형과 전달인자 자료형 구분하기 
  
  ```java
    public static <T> Box<T> makeBox(T o){..}
    // 반환형이 Box<T> 형태이고 전달인자의 자료형이 T
  
    public static <T> T openBox(Box<T> box){...}
   // 반환형이 T이고 전달인자의 자료형이 Box<T>
  
  ```
  
  ### 제네릭 메소드의 제한된 타입 매개변수 선언
  
  제네릭 클래스와 유사하게 제네릭 메소드는 호출 시 전달되는 타입 인자를 제한 가능함.
  
