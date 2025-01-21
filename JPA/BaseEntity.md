## BaseEntity

스프링부트에서 엔티티를 설계하는 과정 중 항상 등장하는 녀석 : `id`

```java
 	  @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
```

Feed, Comment등등 여러 엔티티에 필수적으로 포함되는 createdAt과 updatedAt

```java
    @CreatedDate
    @Column(nullable = false, updatable = false)
    private LocalDateTime createdAt;

    @LastModifiedDate
    @Column(nullable = false)
    private LocalDateTime updatedAt;
```

### 엔티티 설계 작업을 할때마다 반복적으로 나타나는 이 녀석들을 가독성있고 깔끔하게 처리할 수 없을까??

<aside>

🚀 BaseEntity를 이용하면 된다.

</aside>

- **BaseEntity** 클래스는 일반적으로 여러 엔티티 클래스에서 공통으로 사용되는 필드인 **`id`**, **`createdAt`**, **`updatedAt`** 등을 모아놓은 추상 클래스로, 이를 상속받은 구체적인 엔티티 클래스들이 중복된 코드 없이 해당 공통 속성들을 자동으로 물려받을 수 있도록 한다.

```java
@Getter
@MappedSuperclass
@EntityListeners(AuditingEntityListener.class)
public abstract class BaseEntity {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @CreatedDate
    private LocalDateTime createdAt;

    @LastModifiedDate
    private LocalDateTime updatedAt;

}
```

생소한 어노테이션들을 차근차근 알아보자

### **@** MappedSuperclass

---

> JPA에서 사용되는 어노테이션 중 하나로, **상속을 통해 필드를 자식 클래스에 물려주기 위한 목적**으로 사용된다. 이 어노테이션은 **해당 엔티티의 테이블을 생성하지 않고 속성정보를 상속**받을 수 있게 해준다.
> 
- **`@MappedSuperclass`**를 사용하면, 해당 클래스는 데이터베이스 테이블과 매핑되지 않고, **상속받은 자식 클래스에만 필드를 제공**한다.
    - **`@MappedSuperclass`**가 적용된 클래스는 **테이블에 매핑되지 않는다**.
    - 이 클래스는 **다른 엔티티 클래스에 의해 상속**되며, 자식 클래스에 **공통 필드나 메서드**를 제공하는 용도로 사용된다.
    - 부모 클래스의 필드나 메서드는 자식 클래스에 **상속**되지만, 부모 클래스 자체는 데이터베이스 테이블로 존재하지 않는다.

### **@EntityListeners(AuditingEntityListener.class)**

---

> **엔티티 객체의 상태가 변경될 때 자동으로 처리해야 할 동작을 지정**하는 어노테이션이다.
> 
- **JPA Auditing**을 활성화할 때 사용된다. 이 어노테이션을 사용하면, 엔티티가 생성되거나 수정될 때 **자동으로 날짜를 기록**하는 등의 처리를 할 수 있다.

이런식으로 클래스를 만들고

```java
@Getter
@MappedSuperclass
@EntityListeners(AuditingEntityListener.class)
public abstract class BaseTimeIdEntity extends BaseIdEntity{

    @CreatedDate
    @Column(nullable = false, updatable = false)
    private LocalDateTime createdAt;

    @LastModifiedDate
    @Column(nullable = false)
    private LocalDateTime updatedAt;

}
```

@EnableJpaAuditing어노테이션을 **@SpringBootApplication** 클래스에 추가하면 된다.

```java
@SpringBootApplication
@EnableJpaAuditing // Auditing 활성화
public class SpringBootPracticeApplication {

    public static void main(String[] args) {
        SpringApplication.run(SpringBootPracticeApplication.class, args);
    }

}
```
