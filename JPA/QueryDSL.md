<aside>

**🚀 Query dsl이란?** 

</aside>

> QueryDSL은 오픈소스 프로젝트로 JPQL을 Java 코드로 작성할 수 있도록 하는 라이브러리이다.
> 
- Querydsl은 JPQL 쿼리를 쉽고 빠르게 작성할 수 있게 해준다.

### Query dsl을 사용하는 이유가 뭘까??

---

> **자바 코드로 쿼리를 작성**함으로 **컴파일 시점**에 에러를 잡을 수 있다.
> 
- JPQL은 쿼리를 문자열로 작성해야 한다. (문법 모르면 못씀)
- 만약 오타가 있거나 잘못 작성한다해도 컴파일 시점에 에러가 발생하지 않고 런타임 시점에 발생하기 때문에 실행시키기 전에는 잘못된 부분을 알 수 없다. 🤮
    - **`QueryDSL`**은 **자바 코드로 쿼리를 작성**하기 때문에 **컴파일 시점에 에러**를 잡을 수 있다는 큰 장점이 있다.

> **복잡한 동적 쿼리**를 **쉽게** 다룰 수 있다.
> 
- **JPQL**을 이용해 **동적 쿼리**를 다루기 위해서는 문자열을 조건에 맞게 조합해서 사용해야한다.
    - 이는 코드도 복잡해지고 런타임 에러를 발생시키는 치명적인 단점이 있다.

- **`QueryDSL`**은 복잡한 동적 쿼리도 **Q클래스**, **메서드**를 활용하여 쉽게 다룰 수 있다.

### Query dsl 써보기

---

**build** **gradle** **설정**

```java

 dependencies {
	//기타 라이브러리
 
  //QueryDSL 추가
	implementation 'com.querydsl:querydsl-jpa:5.0.0:jakarta'
	annotationProcessor "com.querydsl:querydsl-apt:${dependencyManagement.importedProperties['querydsl.version']}:jakarta"
	annotationProcessor "jakarta.annotation:jakarta.annotation-api"
	annotationProcessor "jakarta.persistence:jakarta.persistence-api"	
}
	
clean {
	delete file('src/main/generated')
}
```

**QuerydslConfig** (**JPAQueryFactory 빈 등록)**

- **QueryDSL**을 사용하려면 **JPAQueryFactory** 객체가 필요하다.
    - Spring Boot 환경에서는 **@PersistenceContext**를 사용해 **EntityManager**를 주입하고 이를 통해 **JPAQueryFactory**를 생성한다.

```java
import com.querydsl.jpa.impl.JPAQueryFactory;
import jakarta.persistence.EntityManager;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class QuerydslConfig {

    @PersistenceContext
    private EntityManager entityManager;

    @Bean
    public JPAQueryFactory jpaQueryFactory() {
        return new JPAQueryFactory(entityManager);
    }
}

```

### JPAQueryFactory

> JPAQueryFactory란 JPA의 엔터티를 이용하여 JPQLQuery를 보다 쉽고 편리하게 작성할 수 있는 QueryDsl의 도구이다.
> 
- JPA 엔티티 매니저(**EntityManager**)를 통해 데이터베이스와 연결한다.

### Q클래스

> 엔티티 클래스의 메타 정보를 담고 있는 클래스로, Querydsl은 이를 이용하여 **타입 안정성(Type safe)**을 보장하면서 쿼리를 작성할 수 있게 된다.
> 
- **JPA_APT(JPAAnnotationProcessorTool)**가 **@Entity** 와 같은 특정 어노테이션을 찾고 해당 클래스를 분석해서 QClass를 만들어 준다.
- 엔티티의 필드를 객체로 변환하여 **쿼리** 작성 시 **문자열 대신 필드 객체**로 접근할 수 있게 해준다.

### 왜 굳이 Q클래스를 사용할까?

- 그냥 엔티티클래스를 사용하면 안되는 걸까?

> **QClass**와 엔티티 클래스는 많은 장점을 공유하고 있지만 그럼에도 **QClass**를 사용하는 이유는…
> 
1. **QClass**는 엔티티 속성을 정적인 방식으로 표현하므로 **IDE**의 자동 완성 기능을 활용할 수 있고, 속성 이름을 직접 기억하거나 확인하지 않아도 된다는 장점을 가지고 있다.
2. **QClass**는 엔티티 속성의 타입을 정확하게 표현하므로, 타입에 맞지 않는 연산이나 비교를 시도하면 **컴파일러가 오류를 감지**할 수 있다.

<aside>

**엔티티 클래스는 데이터베이스 테이블의 매핑을 담당하고, QClass는 쿼리 작성을 위한 편의성과 안전성을 제공을 해주면서 유지보수의 편의성 및 실수 방지를 하지 않도록 해준다.**

</aside>

### APT

> Annotation 이 있는 기존코드를 바탕으로 새로운 코드와 새로운 파일들을 만들 수 있고, 이들을 이용한 클래스에서 compile 하는 기능도 지원해준다.
> 
- ex)  **Lombok의 @Getter, @Setter**
    - 해당 어노테이션을 사용하는 경우 **apt가 컴파일 시점**에 해당 어노테이션을 기준으로 **getter** 와 **setter**를 만들어 주기 때문에 코드를 작성하지 않고 사용이 가능해진다.

### 참고자료

https://velog.io/@evan523/JPA-QueryDSL

https://velog.io/@jkijki12/Spring-QueryDSL-%EC%99%84%EB%B2%BD-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0

https://velog.io/@martindog/Spring-JPAQueryFactory-%EC%9D%B4%EC%9A%A9%ED%95%98%EA%B8%B0

https://ssow93.tistory.com/60

### 보면 좋을 자료

[GitHub - jeongho1209/Study-SpringBoot: SpringBoot 연습한 코드입니다](https://github.com/jeongho1209/Study-SpringBoot)

[GitHub - Team-jeong-ho-kim/Daedongyeojido_BE_v3](https://github.com/Team-jeong-ho-kim/Daedongyeojido_BE_v3)
