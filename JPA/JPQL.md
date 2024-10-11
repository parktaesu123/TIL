### JPQL (Java Persistence Query Language)

---

```kotlin
// 목록 조회
        List<Member> members = em.createQuery("select m from Member m", Member.class).getResultList();
        System.out.println("members.size=" + members.size());
```

- JPA를 사용하면 개발자는 엔티티 객체를 중심으로 개발하고 JPA는 데이터베이스에 대한 처리를 한다.
- 위 코드를 보면 SQL을 전혀 사용하지 않았다.
- 하나 이상의 회원 목록을 조회하는 위 코드 처럼 복잡한 관계를 JPA에서 제공하는 기본 메서드를 이용하여 표현하는 것은 한계가 있다.
- JPA는 엔티티 객체를 대상으로 검색을 수행하므로 모든 테이블을 객체로 변환해서 검색해야 하는데 이 방법은 사실상 불가능하다.

> **애플리케이션이 필요한 데이터만 데이터베이스에서 불러오려면 결국 SQL을 사용해야 한다.**
> 

<aside>
💡

JPQL은 엔티티 객체를 대상으로 쿼리하지만 최종적으로는 SQL로 변환이 되어 데이터베이스에 적용 된다. JPQL이 테이블을 대상으로 쿼리 하는 SQL과 달리 엔티티 클래스와 그 속성(클래스와 필드)을 기반으로 쿼리를 작성한다는 것이다. JPQL은 데이터베이스 구조가 아니라 애플리케이션 도메인 모델에 집중하므로 보다 객체 지향적인 접근을 가능하게 한다.

</aside>

- 위 코드에서 **`select m from Member m`**이 바로 JPQL이다.
- from Member는 회원 엔티티 객체를 말하는 것이지 MEMBER 테이블이 아니다.
- **JPQL은 데이터베이스 테이블을 전혀 알지 못한다.**
- em.createQuery(JPQL, 반환타입) 메서드를 실행해서 쿼리 객체를 생성한 후 쿼리 객체의 getResultList() 메서드를 호출하면 된다.

### JPA는 JPQL을 분석하여 적절한 SQL을 만들어 DB에서 데이터를 조회한다.

```sql
SELECT M.ID, M.NAME, M.AGE FROM MEMBER M //전체 목록 조회
```
