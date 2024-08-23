<aside>
🚀 **Spring Security란??**

</aside>

- **인증**, **권한 관리**, **데이터 보호 기능**을 포함하여 사용자 관리 기능을 구현하는데 도움을 주는 Spring의 framework이다.
- 사용자 관리 부분으로 **회원가입부터 로그인, 로그아웃, 세션 관리, 권한 관리**까지 온라인 플랫폼에 맞춰 다양하게 작업 되는 인가 & 보안 기능을 개발자들이 효율적이고 신속하게 구현할 수 있도록 도와준다.

> **Spring Security를 왜 쓸까요?**
> 
- **Spring Security가 Spring의 생태계에서 보안에 필요한 기능들을 제공하기 때문입니다.**
- Spring에서 제공하는 IOC/DI 패턴과 같은 확장 패턴을 고려하여 인증&인가 부분을 개발하기는 쉽지 않다. → Spring Security가 해결해준다.
- 만약 Spring Securiy를 사용하지 않는다면 직접 session을 체크하고 redirect등을 해야만 한다.

## Authentication객체

- 인증 된 사용자의 상세 정보 → 통행증 역할
- SecurityContextHolder 내부에 SecurityContext에 저장된다.
- **인증 토큰이라고 부른다.**

> **주요 용어**
> 
- **Principal**: 보호 된 리소스에 접근하는 사용자 식별자(아이디)
- **Credentials**: 인증을 위해 필요한 정보(비밀번호)
- **GrantedAuthority**: 인증 된 사용자의 인증 정보(역할 등)을 표현
- **SecurityContext**: Authentication 객체를 포함하고 있으며, SecurityContextHolder를 통해 접근할 수 있다.

## SecurityContextHolder

- 인증된 사용자의 세부 정보를 저장하는 곳 → Authentication객체 저장
- 어떤 값이든지 값을 포함하고 있다면 현재 인증 된 사용자로 사용된다.

### Security 인증 구현

1. `Authentication`을 구현하는 객체인 `Authentication Token` 클래스 인증 정보를 생성
2. 생성된 `Authentication Token` 객체는 `Security context holder`를 통해 `Thread-Local`영역에 저장 

## Thread-Local

- Thread 내부에서 사용되는 지역변수인 `Thread-Local` 변수 제공
- Thread 수준에서 공유하는 데이터 저장소로 파라미터로 넘기지 않더라도 접근이 가능하다.
- Security 외에는 Transaction에 사용된다.

### SecurityContextHolder는 Authenfication 객체를 매개변수로 받지 않아도 Thread-Local에 저장된 Authenficaion(인증 처리된 사용자 정보) 객체를 사용한다.

```java
SecurityContextHolder.getcontext().get Authenfication();
```

### 참고자료

https://www.elancer.co.kr/blog/view?seq=235

[https://e-una.tistory.com/57#1. Authentication](https://e-una.tistory.com/57#1.%20Authentication)
