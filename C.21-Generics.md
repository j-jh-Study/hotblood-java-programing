# 제네릭

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
 
 


