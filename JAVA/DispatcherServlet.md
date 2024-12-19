## 디스패처 서블릿

---

<aside>

**💡 디스패처 서블릿(Dispatcher Sevlet)이란?**

</aside>

> HTTP 프로토콜로 오는 모든 요청을 가장 먼저 받아 요청에 적합한 컨트롤러를 찾아 위임해주는 **`프론트 컨트롤러`**
> 

- 클라이언트로부터 요청이 들어오면 서블릿 컨테이너가 요청을 받고, 그 후에 디스패처 서블릿이 받는다.
- 디스패처 서블릿은 요청을 처리하기 위한 준비와 후속작업을 처리한 후 해당 요청을 처리해야 하는 컨트롤러를 찾아 작업을 위임한다.

## Dispatcher Servlet의 장점

---

> 이전에는 **web.xml**에 서블릿 대한 URL 매핑들을 설정해주어야 하는 번거로운 작업이 필요했다.
이러한 불편함을 **`Dispatcher Sevlet`**이 완화해주어 **web.xml**의 역할을 상당 수 축소시켜주었다.
> 
- Spring MVC의 **`Dispatcher Servlet`**은 모든 요청을 먼저 받아서 공통적인 작업을 처리해주고, 요청에 적합한 컨트롤러를 **어노테이션 기반으로 매핑**한다.
- 개발자가 컨트롤러에 붙인 어노테이션 정보를 바탕으로 적절한 요청 처리를 자동으로 찾아준다.
    - @RestController
    - @RequestMapping 등등

## Dispatcher Servlet의 동작원리

---

1. 클라이언트의 요청을 디스패처 서블릿이 받는다.
2. 요청 정보를 통해 요청을 위임할 컨트롤러를 찾는다.
3. 요청을 컨트롤러로 위임할 핸들러 어댑터를 찾아서 전달한다.
4. 핸들러 어댑터가 컨트롤러로 요청을 위임한다.
5. 비지니스 로직을 처리하고한다.
6. 컨트롤러가 반환값을 반환한다.
7. 핸들러 어댑터가 반환값을 처리한다.
8. 서버의 응답을 클라이언트로 반환한다.

*(자세한 설명은 https://mangkyu.tistory.com/18)*

### 참고자료

https://mangkyu.tistory.com/18

https://zzang9ha.tistory.com/441

https://velog.io/@uiurihappy/%EB%94%94%EC%8A%A4%ED%8C%A8%EC%B2%98-%EC%84%9C%EB%B8%94%EB%A6%BFDispatcher-Servlet