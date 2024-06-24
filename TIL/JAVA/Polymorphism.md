## 타입 변환과 다형성

<aside>
💡 다형성이란?

</aside>

- 사용 방법은 동일하지만 다양한 객체를 이용해서 다양한 실행 결과가 나오도록 하는 성질
- 상속 관계에 있는 클래스들이 동일한 메서드 이름을 사용하면서 각자 다르게 구현된 동작을 수행하는 것
- ex) 자동차가 타이어를 사용하는 방법은 동일하지만 어떤 타이어를 사용하느냐에 따라 성능이 달라질 수 있다.

---

> 다형성을 구현하려면 메소드 재정의와 타입 변환이 필요하다.
> 

<aside>
💡 타입변환이란?

</aside>

- 타입을 다른 타입으로 변환하는 것
- 클래스의 타입변환은 상속 관계에서 발생한다.
    - 자식은 부모 타입으로 자동 타입 변환이 가능하다.

### 자동 타입 변환

- 프로그램 실행 도중에 자동적으로 타입 변환이 일어나는 것
- 자동 타입 변환을 하면 자식은 부모의 특징과 기능을 상속받는다.
    - 고로 부모와 동일하게 취급될 수 있다.
    - ex) 강아지가 동물의 특징과 기능을 상속받았다면 “고양이는 동물이다.”가 성립

```
Cat cat = new Cat();  // cat객체를 생성

Animal animal = cat;  //animal변수에 대입 -> 자동 타입 변환이 일어남
```

- 위에 경우 두변수 모두 동일한 객체(cat)를 참조한다.
- 부모 타입으로 자동 타입 변환된 이후에는 부모 클래스의 필드와 메소드만 접근 가능
    - 변수는 자식 객체를 참조하나, 변수로 접근 가능한 멤버는 부모 클래스 멤버로 한정
    - 예외
        - 메소드가 자식클래스에서 재정의된 경우는 자식클래스의 메소드가 호출됨
### 강제 타입 변환

> 자식 → 부모로 자동 변환된 객체를 다시 부모 → 자식으로 타입 변환 하는 것
> 
- 강제 타입변환은 모든 부모 객체에 적용되는 것이 아니라
- 자동 형변환으로 자식 → 부모 과정이 있었던 부모 객체에만 적용된다.
    - 자식→부모로 부모 타입이 된 객체는 자식 객체를 참조하므로 자식으로의 타입 변환이 가능하다
- 이를 통해 자식 객체의 필드,오버라이딩되지 않은 메소드들도 사용할 수 있다.

```java
Parent parent = new Child(); //자동 타입 변환
Child child = (Child) parent; //강제 타입변환
```
---
> 오버로딩
> 
- 같은 이름의 함수에 매개변수를 다르게 주는 것
- 같은 이름의 함수에 매개변수의 수나 자료형을 다르게 하여 여러 개 선언할 수 있다.

```java
public class Test {

    // 매개변수가 없는 overloadingTest() method
    void overloadingTest(){
        System.out.println("매개변수를 받지 않는 메서드");
    }

    // 매개변수로 int형 인자 2개를 요청하는 overloadingTest(int a, int b) method
    void overloadingTest(int a, int b){
        System.out.println("int형 인자 2개를 요청하는 메서드 "+ a + ", " + b);
    }

    // 매개변수로 String형 인자 1개를 요청하는 overloadingTest(String str) method
    void overloadingTest(String str){
        System.out.println("String형 인자 1개를 요청하는 메서드 " + d);
    }
}
```

---

> 오버라이딩
> 
- 상위 클래스에서 정의된 변수와 메소드의 내용을 하위 클래스에서 변경하여 재정의하는 것

```java
public class Parent {
    public void overridingTest() {
        System.out.println("부모 메서드의 내용");
    }
}
public class Child extends Parent {
    @Override
    public void overridingTest() {
        System.out.println("부모 클래스의 메서드를 상속받아 내용을 재정의해서 사용");
    }
}
```
