## JDBC API

<aside>
🚀 JDBC API란?

</aside>

- **Java DataBase Connectivity**의 약어로 자바와 DB를 연결해 주는 **`통로`**이다.
- JAVA 기반 어플리케이션의 데이터를 데이터베이스에 저장 및 업데이트하거나, 데이터베이스에 저장된 데이터를 JAVA에서 사용할 수 있도록 하는 JAVA API이다.
    - JDBC API를 사용하여 데이터베이스에 연동
    - 데이터베이스에서 자료를 쿼리(Query)하거나 업데이트하는 방법을 제공
  
### JDBC API가 필요한 이유

---

- 기존에 DB를 관리할 때 SQL을 이용하여 DB에 직접 값을 넣거나 조회하는 등의 일을 수행했었다.
    - 하지만 우리가 웹을 동작, 수행 시킬 때마다 그렇게 할 수는 없다.
    - 그래서 프로그램이 대신 해결해주는 것 → JDBC

## JDBC 동작 흐름

- **JDBC 드라이버 로딩** : 사용하고자 하는 JDBC 드라이버를 로딩한다. JDBC 드라이버는 DriverManager 클래스를 통해 로딩된다.
- **Connection 객체 생성** : JDBC 드라이버가 정상적으로 로딩되면 DriverManager를 통해 데이터베이스와 연결되는 세션(Session)인 Connection 객체를 생성한다.
    - **Connection Pool** : Connection 객체를 미리 생성하여 보관하고 애플리케이션이필요할 때 꺼내서 사용할 수 있도록 관리
- **Statement 객체 생성** : Statement 객체는 작성된 SQL 쿼리문을 실행하기 위한 객체로 정적 SQL 쿼리 문자열을 입력으로 가진다.
- **Query 실행** : 생성된 Statement 객체를 이용하여 입력한 SQL 쿼리를 실행한다.
- **ResultSet 객체로부터 데이터 조회** : 실행된 SQL 쿼리문에 대한 결과 데이터 셋이다.
- **ResultSet, Statement, Connection 객체들의 Close** : JDBC API를 통해 사용된 객체들은 생성된 객체들을 사용한 순서의 역순으로 Close 한다.

### 참고자료

[https://velog.io/@jungnoeun/JDBC란](https://velog.io/@jungnoeun/JDBC%EB%9E%80)

https://ittrue.tistory.com/250
