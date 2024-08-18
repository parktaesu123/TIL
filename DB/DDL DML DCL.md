<aside>
💡 **DDL**(Data Definition Language)이란?

</aside>

- 데이터 정의 언어(DDL)은 데이터베이스를 정의하는 언어를 말한다.
- 데이터를 생성,수정,삭제하는 등의 데이터의 전체의 골격을 결정하는 역할을 합니다.

- **CREATE** **:** 데이터베이스, 테이블 등을 생성
- **ALTER** **:** 테이블을 수정
- **DROP** **:** 데이터베이스, 테이블을 삭제
- **TRUNCATE** **:** 테이블을 초기화
- **RENAME** **:** 기존 테이블 이름 변경

⭕ SCHEMA, DOMAIN, TABLE, VIEW ,INDEX를 정의하거나 변경 또는 삭제할 때 사용하는 언어

⭕데이터베이스 관리자나 데이터베이스 설계자가 사용합니다.

---

<aside>
💡 **DML**(Date Manipulation Language)이란?

</aside>

- 데이터 조작어(DML)는 데이터 조작에 사용하는 언어로, 테이블의 데이터를 조회, 저장, 수정, 삭제합니다.
- 테이블에 있는 행과 열을 조작하는 언어이다.

- **SELECT** **:** 저장된 데이터를 조회
- **INSERT** **:** 새로운 데이터를 저장
- **UPDATE** **:** 저장된 데이터를 수정
- **DELETE** **:** 저장된 데이터를 삭제

⭕데이터베이스 사용자가 응용 프로그램이나 질의어를 통하여 저장된 데이터를 실질적으로 처리하는데 사용하는 언어  

### 질의어

- 프로그래밍에서 "질의어"는 사용자의 입력을 나타내는 용어로 사용될 수 있습니다.
- 사용자가 프로그램에게 질문하거나 정보를 요청할 때 입력하는 문장 또는 구문을 가리킵니다. 예를 들어, 사용자가 웹 검색 엔진에 "날씨 어때?" 라고 입력하면 "날씨 어때?"가 질의어가 됩니다.

⭕데이터베이스 사용자와 데이터베이스 관리 시스템 간의 인터페이스를 제공

---

<aside>
💡 **DCL**(Data Control Language)란?

</aside>

- 데이터 제어어(DCL)는 데이터베이스에 대한 접근 권한 제어에 사용하는 언어로, 각종 권한을 부여, 회수한다.
- 권한 관리를 통해 시스템 보안을 유지하는 역할을 한다.

- **GRANT** **:** 특정 데이터베이스 사용자에게 특정 작업에 대한 수행 권한을 부여
- **REVOKE :** 특정 데이터베이스 사용자에게 특정 작업에 대한 수행 권한을 박탈,회수
- **COMMIT :** 트랜잭션의 작업을 저장
- **ROLLBACK :** 트랜잭션의 작업을 취소,원래대로 복구

### 트랜잭션

트랜잭션(Transcation)이란 여러개의 작업을 하나로 묶은 실행 유닛을 말한다.

데이터베이스 관점에서는 데이터베이스의 상태를 변환 시키기 위해서 수행하는 작업의 단위이다.

---

> 위 내용 정리
> 
- **DDL**을 통해 데이터 베이스와 테이블을 생성 및 변경,제거를 하고
- **DML**을 통해 생성된 테이블 내에 있는 데이터들(행과 열)을 입력, 변경,수정 등을 하며
- **DCL**을 통해 데이터 베이스의 접속 권한 등을 수정할 수 있다.