<aside>
🚀 **Transaction이란?**

</aside>

- 데이터베이스의 상태를 변화 시키기 위해서 수행하는 **작업의 단위**이자
- 더 이상 분할이 불가능한 업무 처리의 단위이다.

### 예시

---

> **Transaction이 없는 경우**
> 
- 짱구와 철수는 각각 통장에 10000원씩 있다.
- 짱구가 철수에게 빌린 돈을 갚기 위해 2000원을 보냈다.

- 여기서 문제가 발생한다.
- 짱구는 철수에게 돈을 보냈지만, 돈을 받는 과정에서 문제가 발생해 철수는 돈을 받지 못했다.

> **원래라면 짱구가 철수에게 2000원 계좌 이체를 할 경우 다음과 같은 작업이 이루어져야 한다.**
> 
1. 짱구의 잔고를 2000원 감소 → success
2. 철수의 잔고를 2000원 증가 → 실패하면서 짱구 돈만 날라가는 (레전드)상황 발생

### 위와 같은 상황에서 (계좌 이체)

- 인출은 성공했는데 입금에 실패하면 치명적인 결과가 나온다.
- 따라서 이 두 과정은 동시에 성공하던지 동시에 실패 해야 한다.
- 이러한 과정을 묶는 방법이 **Transaction**이다.

## Transaction의 기능

---

- DB가 제공하는 **Transaction기능**을 사용하면 commit과 rollback으로 정상적인 작업을 진행한다.
- 위처럼 1번은 성공했는데 2번은 실패하는 문제가 발생했을 때 (작업 중 하나라도 실패했을 때) 거래 이전 상태로 돌아가는 것을 rollback이라고 한다.
- 반대로 작업이 성공적으로 진행되었을 경우 데이터베이스에 그 결과를 반영하는 것을 commit이라고 한다.

### 참고자료

[https://inpa.tistory.com/entry/MYSQL-📚-트랜잭션Transaction-이란-💯-정리](https://inpa.tistory.com/entry/MYSQL-%F0%9F%93%9A-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98Transaction-%EC%9D%B4%EB%9E%80-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC)

[https://hstory0208.tistory.com/entry/트랜잭션이란-특징과-사용법에-대해-쉽게-알아보자](https://hstory0208.tistory.com/entry/%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98%EC%9D%B4%EB%9E%80-%ED%8A%B9%EC%A7%95%EA%B3%BC-%EC%82%AC%EC%9A%A9%EB%B2%95%EC%97%90-%EB%8C%80%ED%95%B4-%EC%89%BD%EA%B2%8C-%EC%95%8C%EC%95%84%EB%B3%B4%EC%9E%90)
