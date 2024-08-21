<aside>
🚀 **Dirty Checking이란??**

</aside>

- JPA에서 Transaction이 끝나는 시점에 변경 사향이 있는 모든 엔티티를 DB에 반영시켜주는 것이다.
- Dirty Checking은 상태 변화 검사기를 의미한다.

### Dirty Checking 진행 방식

- 최초 조회 상태를 기준으로 진행한다
- JPA에서 Entity를 조회하면 해당 Entity 조회 상태 그대로 스냅샷을 만든다.
- Transaction이 끝나는 시점에 스냅샷과 비교해서 다른 점이 있으면 Transaction이 commit 되었을 때 Update Query를 DB로 전달한다.

### Dirty Checking의 대상

- 영속성 컨텍스트가 관리하는 엔티티에만 적용이 된다.
- Dirty Checking의 대상이 되지 못하는 엔티티
    - detach된 엔티티 (준영속)
    - DB에 반영되기 전 처음 생성된 Entity (비영속)

### 참고자료

https://jojoldu.tistory.com/415

https://everydayyy.tistory.com/157
