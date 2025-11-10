## **Integrity, 무결성이란?**

- 데이터가 정해진 규칙, 틀에 맞게 완전히 부합하여 신뢰할 수 있는 상태
- 데이터 모델링에서 지향하는 방향으로 값이 정확한 상태를 의미한다.
- **Entity Integrity, Domain Integrity, Referential Integrity, Business Integrity가 존재한다.**

### 무결성 모음

### Entity Integrity

- **기본키(Primary Key)** 가 반드시 존재해야 하며, **NULL이거나 중복되면 안된다.**
- 하나의 행은 반드시 고유해야 한다.

### **Domain Integrity**

- **Column(속성)에 저장되는 값이 미리 설계된 틀과 일치해야야 한다**
- 도메인을 벗어나면 안된다.

### **Referential Integrity**

- 테이블간의 관계가 일관되게 유지되어야 하므로 외래키(Foreign Key) 는 반드시 존재하는 기본키(Primary Key) 를 참조해야 한다.

### **Business Integrity**

- **비즈니스 규칙에 따라 데이터가 일관되게 유지되어야 한다.**
- 규칙에 맞지 않는 말이 안되는 상황이 발생하면 안됨
- ex) 상품 재고가 0인데 주문이 생성됨, 은행 계좌의 잔액이 음수가 됨

## **Consistency, 정합성이란?**

- 데이터가 특정 상황이나 작업 과정에서 논리적인 규칙에 따라 일관되게 유지되는 상태
- 테이블, 데이터 사이에 관계속에서 정해진 규칙에 따라 일관적이여야 한다.
- 정합성은 유지되어도 무결성이 위반될 수 있음

## **Anomaly, 이상현상?**

- 정합성은 유지되지만 무결성이 위반되는 상태
- 정규화가 되어있지 않은 중복된 데이터가 많은 상태에서 주로 발생한다.

### 참고자료

https://spidyweb.tistory.com/164

https://velog.io/@yangsijun528/%EB%AC%B4%EA%B2%B0%EC%84%B1%EA%B3%BC-%EC%A0%95%ED%95%A9%EC%84%B1%EC%9D%B4%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80

https://inpa.tistory.com/entry/DB-%F0%9F%93%9A-%EB%AC%B4%EA%B2%B0%EC%84%B1-%EC%A0%9C%EC%95%BD-%EC%A1%B0%EA%B1%B4-%F0%9F%95%B5%EF%B8%8F-%EC%A0%95%EB%A6%AC#thankYou

https://dev-coco.tistory.com/63#google_vignette
