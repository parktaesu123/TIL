## 영속성 컨텍스트

<aside>

💡 영속성 컨텍스트란?

</aside>

- 영속성 컨텐스트란 **엔티티를 영구 저장하는 환경**이라는 뜻이다.
- 애플리케이션과 데이터베이스 사이에서 객체를 보관하는 가상의 데이터베이스 같은 역할을 한다.
- 엔티티 매니저를 통해 엔티티를 저장하거나 조회하면 엔티티 매니저는 영속성 컨텍스트에 엔티티를 보관하고 관리한다.

```sql
em.persist(member);
//엔티티 매니저를 사용해서 회원 엔티티를 영속성 컨텍스트에 저장
```

  
### 엔티티 매니저

> 엔티티를 저장하고, 수정하고, 삭제하고, 조회하는 등 엔티티와 관련된 모든 일을 처리한다. 엔티티를 관리하는 관리자, 엔티티를 저장하는 가상의 데이터베이스
> 

### 엔티티 매니저 팩토리

> 엔티티 매니저를 만드는 공장,
공장을 만드는 비용은 상당히 크다.
반면 공장에서 엔티티 매니저를 생성하는 비용은 거의 들지 않는다.
> 

### 영속성 컨텍스트의 특징

---

<aside>

**영속성 컨텍스트와 식별자 값**

- 영속성 컨텍스트는 엔티티를 식별자 값으로 구분
- 영속 상태는 식별자 값이 반드시 있어야 함
</aside>

<aside>

**영속성 컨텍스트와 데이터베이스 저장**

- 트랜잭션을 커밋하는 순간 영속성 컨텍스트에 새로 저장된 엔티티를 데이터베이스에 반영
- 위 과정을 플러시(flush)라고 한다.
</aside>

<aside>

**영속성 컨텍스트가 엔티티 관리 장점**

- 1차 캐시
- 동일성 보장
- 트랜잭션을 지원하는 쓰기 지원
- 변경 감지
- 지연 로딩
</aside>
