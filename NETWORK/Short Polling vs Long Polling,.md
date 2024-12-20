# short polling vs long polling

<aside>

🚀 폴링(Polling)이란?

</aside>

- 리얼타임 웹을 위한 기법으로 일정한 주기(특정한 시간)를 가지고 서버와 응답을 주고받는 방식이다.
    - 리얼타임 웹 : 사용자와 서버 간에 데이터를 실시간으로 주고받는 웹 기술
    - 일반적으로는 클라이언트(브라우저)가 요청을 보낼 때만 서버가 응답을 보내는 방식이 사용된다.
    - 반면 리얼 타임 웹은 클라이언트와 서버가 **항상 연결된 상태**로, 새로운 데이터가 발생하면 **즉시 업데이트**가 이루어지는 방식이다.
    
    > 리얼타임 웹의 특징
    - **즉각성 :** 서버에서 데이터가 변경되면 클라이언트에게 즉시 전달
    **- 양방향 통신 :** 클라이언트와 서버 간에 데이터를 주고받을 수 있음
    **- 연속성 :** 연결이 끊기지 않고 지속적으로 데이터를 주고받아야 하는 환경에서 사용
    > 

> 폴링의 문제점 : 
- 폴링의 주기가 짧으면 서버의 성능에 부담이 간다. (오버헤드/트래픽)
- 주기가 길면 실시간성이 떨어진다.
> 

## Short Polling

<aside>

💡 짧은 폴링(Short Polling)이란?

</aside>

- 클라이언트가 **일정한 짧은 주기로 지속해서 요청을 보내고**, 서버에서 줄 새로운 데이터가 없는 경우 빈 응답을, 있는 경우 데이터를 담은 응답을 보내주는 방식이다.
- 빈 응답을 받은 클라이언트는 일정 시간동안(Interval) 기다렸다가 다음 요청을 서버에게 전송한다.
    
> 문제점은 서버가 줄 데이터가 없음에도 계속 요청과 응답 작업을 반복하기 때문에 **불필요한 트래픽**이 많이 발생한다는 것과 이벤트가 발생했을 때 알려주는 것이 아니라 단순히 일정 주기를 두고 요청과 응답이 오가기 때문에 이벤트 발생을 **실시간으로 반영하지 못한다는 것**이다.
> 

## Long Polling

<aside>

💡 긴 폴링(Long Polling)이란?

</aside>

- 서버에서 클라이언트에게 줄 데이터가 없는 경우 곧바로 **응답하지 않고 커넥션을 계속 유지**하며,**서버에서 줄 데이터가 생겼을 때야 응답을 보내는** 방식이다.
- 서버는 보내줄 이벤트나 데이터가 없을 경우 바로 빈 응답을 리턴하지 않고 데이터가 생기거나 이벤트가 발생할 때까지 기다린다. 보내줄 이벤트가 발생하면 그 때 응답을 만들어서 클라이언트에게 전달하고, 클라이언트는 서버가 응답을 줄 때까지 기다렸다가 응답을 받아 이벤트나 데이터를 처리하면 된다.
    
> 짧은 폴링 방식에 비해 불필요한 요청과 응답을 반복하지 않아도 되고,서버에게 이벤트가 발생하면 바로 응답을 주기 때문에 짧은 폴링에 비해 이벤트의 실시간성이 잘 보장된다는 장점이 있다.
> 

<aside>

**클라이언트와 연결을 계속 유지하는 동안 서버 자원을 지속해서 소모**하고 클라이언트에서 먼저 요청을 보내야만 데이터를 받을 수 있다는 단점이 있다.

</aside>

### 참고자료

https://usingsystem.tistory.com/45

https://hbase.tistory.com/473#google_vignette

https://velog.io/@idonymyeon/%EC%95%8C%EB%A6%BC-%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0-1-%EC%95%8C%EB%A6%BC%EC%9D%84-%EA%B5%AC%ED%98%84%ED%95%98%EB%8A%94-%EB%8B%A4%EC%96%91%ED%95%9C-%EB%B0%A9%EB%B2%95
