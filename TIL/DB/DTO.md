> **DTO**
> 
- DTO(Data Transfer Object) 데이터 전송 객체이다.
- DB에서 데이터를 얻어 Service나 Controller 등으로 보낼 때 사용하는 객체를 말한다.
- DTO는 로직을 갖고 있지 않는 순수한 데이터이며, Getter/Setter만을 갖는다.
- 주로 **요청(Request)**과 **응답(Response)**으로 DTO를 선언한다.
---
> **DTO와 Entity의 분리**
> 

<aside>
💡 DTO대신 Entity를 활용하면 편리하지 않을까??

</aside>

- DTO에는 클라이언트가 요청하는 데이터와 그에 따른 서버의 응답 데이터가 있다.
- Entity가 DTO의 역할도 수행하면 **Entity의 책임**이 너무 커지게 된다.
- Entity에서 **요청과 응답 과정**을 할 때 필요하지 않는 데이터도 존재하기 때문에 통신하는데 불필요한 문제가 발생할 수 있다.
