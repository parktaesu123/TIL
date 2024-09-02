## @Configuration

<aside>
🚀

@Configuration 이란?

</aside>

- Spring에서 **Bean을 수동으로 등록**하기 위해서 사용되는 Annotation
- 클래스위에 `@Configuration`을 추가하고, `@Bean`을 사용하여 빈을 수동으로 등록한다.
- 메서드 이름이 빈의 이름이 되므로 중복되지 않게 주의 해야 한다.

> `@Configuration`의 내부를 보면 `@Component`가 있다.
따라서 해당 클래스를 빈으로 등록하고, 클래스의 본문을 파싱해서 `@Bean`이 붙어 있는 메서드를 찾아 빈으로 생성한다.
> 

### @Configuration의 역할

1. **빈을 등록할 때 싱글톤이 되도록 보장해준다.**
    - @Configuration없이 @Bean만 사용하면 스프링 빈으로 등록은 되지만 싱글톤이 유지 되지는 않는다.
    - **싱글톤 보장**
        - 스프링은 CGLIB라는 바이트코드 조작 라이브러리를 사용하여 AppConfig를 상속받은 임의의 proxy클래스를 만들고, 그 다른 클래스를 스프링 빈으로 등록

        - AppConfig를 상속한 Proxy AppConfig를 스프링 빈으로 등록 → 싱글톤 보장
        
        - @Bean이 붙은 메서드 마다 이미 스프링 빈이 존재하면 존재하는 빈을 반환하고, 스프링 빈이 없으면 생성해서 스프링 빈으로 등록하고 반환하는 코드가 동적으로 만들어짐
        - **싱글톤 보장**
        
2. 스프링 컨테이너에서 빈을 관리할 수 있게 된다.

### 참고자료

https://blogshine.tistory.com/551
