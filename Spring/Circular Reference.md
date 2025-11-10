## 순환참조란

- 두 개이상의 객체(빈)이 서로를 참조(의존)하며 무한 순환을 반복하는 구조이다.
- 스프링에서 어떤 스프링 빈을 먼저 만들어야 할 지 결정할 수 없게되는 상황이 발생한다.
    - **`BeanCurrentlyInCreationException`**
- 또한 런타임 상황에서 순환참조 구조에 의한 조회 쿼리가 계속해서 발생하는 문제가 생길 수 있다.

```java
@RequiredArgsConstructor
@Service
public class ServiceA {

    private final ServiceB serviceB;

    public void methodA() {
        serviceB.methodB();
    }
    
}

@RequiredArgsConstructor
@Service
public class ServiceB {

    private final ServiceA serviceA;

    public void methodB() {
        serviceA.methodA();
    }
    
}

```

### 해결 방법

- 의존관계에서 추상화된 인터페이스를 의존하도록 변경하는 DIP
- 빈을 즉시 생성하지 않고 프록시를 통해 조회하여 생성시점을 필요한 경우로 미루는 지연로딩을 통한 해결
    - **`@Lazy`**

### More Deep

- A 객체가 B객체를 의존한다는 것은 A객체가 B객체를 사용하는 것을 의미한다. 이는 B객체의 변경에 대한 영향을 A객체 받을 수 있는 가능성을 열어두는 것이다.
- 무언가를 의존한다는 것은 생각보다 많은 책임을 요구한다. 그렇기에 클린 아키텍쳐에서는 고수준으로 갈수록 추상화 수준을 높이고, 의존성의 방향을 바깥에서 안쪽으로 고정하여 외부 변화로부터 내부 핵심 로직이 영향을 미치지 않도록 한다.

### 참고자료

https://siyoon210.tistory.com/170

https://curiousjinan.tistory.com/entry/spring-circular-references

https://catsbi.oopy.io/4d728131-93cd-4814-994c-65e372f2aef5

https://jxxhxxxmldiary.tistory.com/306
