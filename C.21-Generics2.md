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
컴파일러의 추론능력이 자바 7부터 향상 되었다 .!
  
  ```
  Box<Integer> iBox = EmptyBoxFactory.<Integer>makeBox();
  
  Box<Integer> iBox = EmptyBoxFactory.makeBox();
  ```
  T 를 추론할때 사영 된정보 Box<Integer> 같은 애들을 타켓 타입이라고함!
 
 >여기서 의의는 대입 연산자의 왼편에 있는 정보를 가지고 컴파일러가 이러한 유추를 진행했다는점..
  
  
  ### 와일드카드(Wildcard)
  
  코드의 간결성이 증가한다..
  
 ```
  T대신 object를 쓰면 안되는이유 
  Box<Object>와 Box<String>은 상속 관계를 형성하지 않는다..! 이걸 기억해야함..!
  ```
  
  
