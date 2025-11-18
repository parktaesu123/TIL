## Proxy Pattern

- 실제 객체를 직접 사용하는 것이 아닌, 그 객체를 대신해 요청을 처리하는 
대변/대리 역할의 가짜 객체를 통해 작업을 수행한다.
- 프록시라는 가짜 객체(대리)를 통해 실제 객체에 대한 접근을 제어하며 부가 기능을 처리할 수 있다.

## Proxy Example

> 신용카드는 은행계좌에 대한 프록시이고, 은행계좌는 현금에 대한 프록시이다.
소비자는 결제를 할 때 직접 현금을 통해 결제 하지 않아도 되어 편리함과 안정성을 제공받을 수 있다.
> 

## Proxy Code

```java
interface ObjectInterface {

    void function();
}

class Object implements ObjectInterface { 

		@Override
    public void function() {
		    System.out.println("객체 기능 수행");
	  }
}
```

실제 객체에 대한 인터페이스를 구현한 뒤, 프록시 객체가 인터페이스에 의존하도록 하여 실제 Target 객체의 변화에 대한 영향을 미치지 않도록 한다. (OCP 지향)

DIP(의존성 역전 원칙)의 핵심: 클라이언트는 추상화에만 의존하고, 구현체에는 의존하지 않아야 한다.

```java
class ProxyObject implements ObjectInterface {

    private ObjectInterface objectInterface;
    
    public ProxyObject(ObjectInterface objectInterface) {
	      this.objectInterface = objectInterface;
    }
    
    @Override
    public void function() {
        objectInterface.function();
     
        System.out.println("프록시 기능 수행");    
    }
    
class Client {
    public static void main(String[] args) {
        ObjectInterface objectInterface = new ProxyObject(new Object());
        objectInterface.function();
    }
```

## Proxy Type

- 가상 프록시
    
    <aside>
    
    무거운 객체의 생성 시점을 필요한 시점으로 미루기 위해 사용하는 프록시
    프록시(가짜)객체를 이용하여 실제 객체가 생성된 것처럼 동작할 수 있다.
    실제 객체의 생성에 많은 자원이 소모 되지만 사용 빈도는 낮을 때 쓰는 방식
    
    </aside>
    

- 보호 프록시
    
    <aside>
    
    실제 객체에 대한 접근 권한을 제어하기 위해 사용하는 프록시
    
    사용 권한이 있는 클라이언트의 요청만 허용되도록 프록시가 요청을 가로채고 필터링 작업을 진행
    
    </aside>
    

- 원격 프록시
    
    <aside>
    
    실제 객체가 원격 서버에 존재하는 경우 해당 객체를 로컬 객체처럼 호출할 수 있게 해주는 프록시
    
    프록시가 네트워크 통신을 대신 처리하여 클라이언트는 원격 호출의 복잡함을 알지 못하고 메서드 호출을 통해 사용
    
    </aside>
    

## **Lazy Loading With** JPA **Proxy**

- 엔티티 간에 연관관계가 있을 때, 지연 로딩(Lazy)이 설정되어있으면 JPA는 실제 엔티티 대신 해당 엔티티의 id만 가진 프록시 (가짜)객체를 먼저 반환한다.
- 이 프록시 객체는 실제 데이터가 필요하지 않은 동안에는 DB 조회를 수행하지 않고, 프록시가 가진 target 객체의 id로만 객체가 존재하는 것처럼 동작한다. 연관 객체의 실제 필드가 필요한 순간에 프록시가 DB에 조회 쿼리를 날려서 원본(Target) 엔티티를 불러오는 작업을 수행한다.
- 프록시를 통한 지연로딩은 n+1을 해결하는 근본적인 방법이 아닌 필요한 시점까지 DB 조회를 늦추는 방안일 뿐이다. n+1을 방지하고 해결하고 싶다면 fetch join, batch size 등의 최적화 기법을 사용해야 한다.

### 참고자료

https://inpa.tistory.com/entry/GOF-%F0%9F%92%A0-%ED%94%84%EB%A1%9D%EC%8B%9CProxy-%ED%8C%A8%ED%84%B4-%EC%A0%9C%EB%8C%80%EB%A1%9C-%EB%B0%B0%EC%9B%8C%EB%B3%B4%EC%9E%90

https://velog.io/@newtownboy/%EB%94%94%EC%9E%90%EC%9D%B8%ED%8C%A8%ED%84%B4-%ED%94%84%EB%A1%9D%EC%8B%9C%ED%8C%A8%ED%84%B4Proxy-Pattern

https://refactoring.guru/ko/design-patterns/proxy
