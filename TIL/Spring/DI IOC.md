<aside>
💡 의존성 주입이란?

</aside>

> 어떤 객체에 스프링 컨테이너가 또 다른 객체와 의존성을 맺어주는 행위
> 
- 의존성 주입은 객체 지향 프로그래밍에서 의존하는 객체를 직접 생성하거나 관리하지 않고 외부에서 주입받는 것을 의미한다.
- 즉, 의존성을 클래스 내부에서 생성하거나 결정하지 않고, 외부에서 주입받아 사용하는 방식이다.

```
의존 관계가 변경되지 않을 경우 : 생성자 주입
의존 관계가 선택적이거나 변경 가능한 경우 : 수정자 주입(setter 주입)
```
---
<aside>
💡 제어의 역전이란?

</aside>

> 스프링 컨테이너가 필요에 따라 개발자 대신 Bean들을 관리(제어)해주는 행위
> 
- 일반적인 상황에서는 개발자가 직접 객체를 제어해야 했다. new 연산자를 통해 객체를 생성하고, 객체의 의존성을 맺어주고, 초기화를 해주고 등등...
- 하지만 Spring 에서는 xml파일 또는 어노테이션 방식으로 스프링 컨테이너에 Bean(객체)를 등록하기만 하면, 스프링 컨테이너에서 Bean의 생명주기(생성 -> 의존성 설정 -> 초기화 -> 소멸)를 전부 관리해준다.
- 즉, **객체에 대한 제어권이 컨테이너로 역전**되기 때문에 제어의 역전이라고 하는 것이다.