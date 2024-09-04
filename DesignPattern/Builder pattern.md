## Builder 패턴

<aside>
🚀

Builder pattern이란?

</aside>

- 복잡한 **객체의 생성 과정**과 **표현 방법**을 분리하여 다양한 구성의 인스턴스를 생성하는 생성 패턴
- 생성자의 들어갈 `매개변수`를 메서드에서 받아 마지막에 통합 빌드해서 객체를 생성하는 방식
- **객체의 생성 코드와 상용 코드를 분리**하여 가독성과 유지 보수에 용이하다.

> **예시**
> 

샌드위치를 주문할 때 빵이나 패티 등 속재료들은 주문하는 사람에 의해 마음대로 결정된다.

어떤 사람은 토마토를 빼달라고 할 수 있고 양상추를 빼달라고 할 수도 있다.

이처럼 선택적 속재료들을 보다 유연하게 받아 다양한 타입의 인스턴스를 생성할 수 있어,

**클래스의 선택적 매개변수가 많은 상황에서 유용하게 사용된다.**

### 점층적 생성자 패턴

- 필수 매개변수와 함께 선택 매개변수를 0개, 1개 … 받는 형태로, 다양한 매개변수를 입력받아 인스턴스를 생성하고 싶을 때
- 사용하던 생성자를 오버로딩 하는 방식
- **단점:** 타입이 다양할수록 생성자 메서드 수가 기하급수적으로 증가하여 가독성이나 유지보수 측면에서 좋지 않음

### 코드

```java
class Hamburger {
    // 필수 매개변수
    private int bun;
    private int patty;

    // 선택 매개변수
    private int cheese;
    private int lettuce;
    private int tomato;
    private int bacon;

    public Hamburger(int bun, int patty, int cheese, int lettuce, int tomato, int bacon) {
        this.bun = bun;
        this.patty = patty;
        this.cheese = cheese;
        this.lettuce = lettuce;
        this.tomato = tomato;
        this.bacon = bacon;
    }

    public Hamburger(int bun, int patty, int cheese, int lettuce, int tomato) {
        this.bun = bun;
        this.patty = patty;
        this.cheese = cheese;
        this.lettuce = lettuce;
        this.tomato = tomato;
    }
    

    public Hamburger(int bun, int patty, int cheese, int lettuce) {
        this.bun = bun;
        this.patty = patty;
        this.cheese = cheese;
        this.lettuce = lettuce;
    }

    public Hamburger(int bun, int patty, int cheese) {
        this.bun = bun;
        this.patty = patty;
        this.cheese = cheese;
    }

    ...
}

```

### 자바 빈 패턴

- 매개변수가 없는 생성자로 객체 생성후 Setter 메소드를 이용해 클래스 필드의 초깃값을 설정하는 방식
- **단점:** 외부적으로 Setter 메소드를 노출하고 있으므로, 협업 과정에서 언제 어디서 누군가 Setter메서드를 호출해 함부로 객체를 조작할 수 있다

### 코드

```java
class Hamburger {
    // 필수 매개변수
    private int bun;
    private int patty;

    // 선택 매개변수
    private int cheese;
    private int lettuce;
    private int tomato;
    private int bacon;
    
    public Hamburger() {}

    public void setBun(int bun) {
        this.bun = bun;
    }

    public void setPatty(int patty) {
        this.patty = patty;
    }

    public void setCheese(int cheese) {
        this.cheese = cheese;
    }

    public void setLettuce(int lettuce) {
        this.lettuce = lettuce;
    }

    public void setTomato(int tomato) {
        this.tomato = tomato;
    }

    public void setBacon(int bacon) {
        this.bacon = bacon;
    }
}

```

### Builder 패턴 = 점층적 생성자 패턴 장점 + 자바 빈 패턴 장점

<aside>
💡

**빌더 패턴**은 별도의 **Builder 클래스**를 만들어 메소드를 통해 `step-by-step`으로 값을 입력받은 후에 최종적으로 **build() 메소드**로 하나의 인스턴스를 생성하여 리턴하는 패턴이다.

**빌더 클래스**의 메서드를 `체이닝`형태로 호출함으로써 자연스럽게 인스턴스를 구성하고 마지막에 **build() 메서드**를 통해 최종적으로 객체를 생성한다.

</aside>

### Builder 패턴의 장점

---

1. **필수 멤버와 선택적 멤버를 분리 가능**
2. **객체 생성 단계를 지연할 수 있음**
3. **멤버에 대한 변경 가능성 최소화**
4. **객체 생성 과정을 일관된 프로세스로 표현**

### Builder 패턴의 단점

---

1.  **코드 복잡성 증가**
2. **생성자 보다는 성능은 떨어진다**
3. **지나친 빌더 남용은 금지**

### 참고자료

[https://inpa.tistory.com/entry/GOF-💠-빌더Builder-패턴-끝판왕-정리](https://inpa.tistory.com/entry/GOF-%F0%9F%92%A0-%EB%B9%8C%EB%8D%94Builder-%ED%8C%A8%ED%84%B4-%EB%81%9D%ED%8C%90%EC%99%95-%EC%A0%95%EB%A6%AC)
