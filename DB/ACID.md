<aside>
🚀 **Transaction의 특징 ACID**

</aside>

- Transaction은 **ACID**라고 하는 원자성, 일관성, 격리성, 지속성을 보장해야 한다.

## 원자성 (Atomicity)

- Transaction내에서 실행한 작업들은 **하나의 작업**처럼 모두 성공하거나 모두 실패해야 한다.
- 만약 Transaction 단위로 데이터가 처리되지 않는다면, 짱구 예시와 같은 상황이 발생할 수 있다.

## 일관성(Consistency)

- Transaction의 작업 처리 결과가 항상 일관성이 있어야 한다는 것이다.
- 데이터베이스에서 정한 무결성 제약 조건을 상상 만족해야 한다.
- Transaction이 진행되는 동안에 데이터베이스가 변경되더라도 업데이트된 데이터베이스로 진행되는 것이 아니라 처음에 Transaction을 진행 하기 위해 참조했던 데이터베이스로 진행한다.

## 격리성 (Isolation)

- 독립성은 둘 이상의 Transaction이 동시에 실행되고 있을 경우 어떤 하나의 Transaction이라도, 다른 Transaction의 연산에 끼어들 수 없다는 것이다.
- 하나의 **특정 Transaction**이 완료될 때까지, 다른 **Transaction**이 특정 **Transaction**의 결과를 참조할 수 없다.

## 지속성 (**Durability)**

- Transaction이 성공적으로 완료되었을 경우, 결과는 영구적으로 반영되어야 한다는 것이다.

### 참고자료

[https://inpa.tistory.com/entry/MYSQL-📚-트랜잭션Transaction-이란-💯-정리](https://inpa.tistory.com/entry/MYSQL-%F0%9F%93%9A-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98Transaction-%EC%9D%B4%EB%9E%80-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC)
