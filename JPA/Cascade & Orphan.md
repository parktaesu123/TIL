## BackGround Knowledge

- 영속성 컨텍스트 : 엔티티를 저장하고 실제 데이터베이스와 동기화 되는 환경
- 엔티티 매니저 : 엔티티와 테이블을 매핑하고 엔티티를 관리하는 역할
- 영속성 컨텍스트에서 관리되는 엔티티들은 영속 상태이다.

## 영속성 전이란?

- 특정 엔티티의 영속성이 다른 엔티티로 전이되는 기능
- 엔티티 간의 연관관계를 형성하고 있을때 부모와 자식 엔티티를 각각 영속화 작업을 진행하는 것이 아닌 한 번에 영속화 하는 기능이다.
- 연관관계 설정 + cascade를 통해 설정할 수 있다.
- 저장과 마찬가지로 cascade 설정을 통해 부모 엔티티를 삭제할 때 연관된 자식 엔티티들도 함께 삭제할 수 있다.

ex)

```java
    @OneToMany(mappedBy = "club", cascade = CascadeType.ALL)
    private List<ClubMajor> majors = new ArrayList<>();
```

## Cascade Option

| ALL (모두 적용) | 아래 모든 동작을 포함하는 종합 옵션 |
| --- | --- |
| PERSIST (영속화) | 부모 엔티티가 영속 상태가 될 때, 자식 엔티티도 영속 상태가 된다. |
| MERGE (병합) | 부모 엔티티가 병합될 때, 자식 엔티티도 병합된다. |
| REMOVE (삭제) | 부모 엔티티가 삭제될 때, 자식 엔티티도 삭제된다. |
| REFRESH (새로고침) | 부모 엔티티가 새로고침 될 때, 자식 엔티티도 자동으로 새로고침된다. (= DB 동기화) |
| DETACH (분리) | 부모 엔티티가 영속성 컨텍스트에서 분리될 때, 자식 엔티티도 분리된다. |

## 고아 객체란?

- 부모 엔티티와 연관관계가 끊어진 상태의 자식 엔티티
- JPA는 연관 관계가 끊어질 때 자식 엔티티를 자동으로 삭제해주는 고아 객체 제거 기능을 지원해준다.
- @OneToOne과 @OneToMany에서 사용가능하다
- 부모 엔티티를 삭제해도 자식 엔티티는 고아 객체가 되기 때문에 orphanRemoval = true을 통해 CascadeType.REMOVE와 동일한 기능을 제공한다.

ex)

```java
    @OneToMany(mappedBy = "club", cascade = CascadeType.ALL, orphanRemoval = true)
    private List<ClubMajor> majors = new ArrayList<>();
```

## mappedBy = “”

- 이 필드는 반대쪽 엔티티에 의해 매핑되는 필드로 연관관계의 주인이 아님을 명시한다.
- 반대 테이블에서 외래키를 관리한다.
- 순환참조를 방지할 수 있다.

### 참고자료

https://hogwart-scholars.tistory.com/entry/JPA-%EC%98%81%EC%86%8D%EC%84%B1-%EC%A0%84%EC%9D%B4-CASCADE%EC%99%80-%EA%B3%A0%EC%95%84-%EA%B0%9D%EC%B2%B4%EC%97%90-%EB%8C%80%ED%95%98%EC%97%AC
