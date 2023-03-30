# 제네릭 2

## 목차


## 22-1 제네릭 심화문법

### 제네릭 클래스와 상속

SteelBox<T> extend  Box<T> 할 수있다 .. ! 
그러면..
SteelBox<Integer> -> Box<Integer> 
  즉  이러면 
  ```
 Box<Integer> box = new SteelBox<Integer>
  ```
  
  => SteelBox<Integer> 제네릭 타입(매겨변수화 타입) 은 Box<Integer> 제네릭 타입을 상속한다

  이것도 가능한가 ?
  ```
  Box<Number> box = new Box<Integer>();
  ```
Number를 Integer가 상속하지만 Box<Number> 와 Box<Integer>는 상속 관계를 형성하지 않는다 따라서 컴파일되지 않는다
  
  
 ### 타겟타입(Target Types)
  
  
