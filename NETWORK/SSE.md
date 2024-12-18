### 나는 SSE를 왜 공부하게 되었는가?
---
> 프로젝트에서 실시간 알림 기능을 구현하기 위해서이다.
> 
- 알림 기능은 기존처럼 클라이언트가 서버에게 요청을 보내는 방식이 아니라, 서버에서 클라이언트에게 데이터를 보내면 클라이언트가 이를 받고 실시간으로 적용하는 방식으로 이루어진다.
- 따라서 알림을 구현하기 위해서는 **`SSE`**와 같은 방식이 적합하다.

### 이러한 개념이 필요한 이유는?
---
> **`HTTP 프로토콜`**의 주요 특징인 **비연결성** 때문이다
> 
- HTTP 프로토콜은 **클라이언트와 서버가 한 번 연결을 맺은 후, 클라이언트 요청에 대해 서버가 응답을 마치면 맺었던 연결을 끊어 버리는 비연결성**을 주요 특징으로 가지고 있다.
- 따라서 Server가 데이터를 전송하고 싶어도 Client와 지속적으로 연결이 되어있지 않기 때문에 보낼 수 없는 상황이 발생하게 된다.

## 서버 전송 이벤트(Server Sent Events)

<aside>

💡 **SSE(Server Sent Events)란?**

</aside>

> 서버에서 이벤트가 발생했을 때 실시간으로 클라이언트로 데이터를 넘겨 주는 실시간 단방향 통신 방법
> 
- **`SSE`**는 클라이언트에서 서버로 요청을 보내면 서버에서 일정시간동안 커넥션 연결을 유지한다.
- `SSE`는 서버에서 응답을 하든 안하든 일정시간동안 연결을 유지한다.
    - vs Long polling
        
        > 클라이언트와 서버가 연결을 유지한다는 점에서 Long polling과 유사하다고 느낄 수 있지만,
        > 
        - Long polling은 서버에서 이벤트가 발생해 데이터를 응답하면, 연결이 끊어지고 다시 연결해야 하지만 **`SSE`**는 서버에서 데이터를 응답하든 말든 일정 시간 동안은 연결을 끊지 않고 계속 유지한다는 차이가 있다.
        
<aside>

- Spring Boot를 이용할 경우 별도의 라이브러리를 사용하지 않아도 스프링에서 SSE를 제공해준다. → https://tecoble.techcourse.co.kr/post/2022-10-11-server-sent-events/
- Spring Framework는 4.2부터 `SseEmitter` 클래스를 제공하여, **서버 사이드에서의 SSE 통신 구현**이 가능해졌다.
</aside>

### 참고자료

https://velog.io/@alswn9938/SSE%EB%9E%80

https://velog.io/@idonymyeon/%EC%95%8C%EB%A6%BC-%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0-1-%EC%95%8C%EB%A6%BC%EC%9D%84-%EA%B5%AC%ED%98%84%ED%95%98%EB%8A%94-%EB%8B%A4%EC%96%91%ED%95%9C-%EB%B0%A9%EB%B2%95

https://gilssang97.tistory.com/69?category=1065324

https://victorydntmd.tistory.com/286
