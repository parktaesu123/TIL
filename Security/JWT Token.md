# JWT Token


<aside>
🚀 **JWT Token이란?**

</aside>

- **JWT(Json Web Token)**은 Json 객체에 인증에 필요한 정보들을 담은 후 **비밀 키**로 서명한 토큰으로, 인터넷 표준 인증 방식이다. 공식적으로 **인증(Authentication) & 권한 허가(Authorization)** 방식으로 사용된다.

### JWT Process



1. 사용자가 아이디와 비밀번호 혹은 소셜 로그인을 이용하여 서버에 로그인 요청을 보낸다.
2. 서버는 **비밀 키**를 사용하여 Json객체를 암호화한 **JWT Token**을 발급한다.
3. JWT를 **헤더**에 담아 클라이언트에 보낸다.

## Access Token과 Refresh Token

- JWT  Token을 탈취 당했을 때 JWT 토큰을 탈취한 사람은 마치 신뢰할만한 사람인 것처럼 인증을 통과할 수 있으므로 주인인 클라이언트와 탈취한 사람을 서버는 구분할 수 없다. 따라서 **유효 기간**을 두어야 하는 것이다.
- 그런데 유효 기간을 짧게 두면 사용자가 로그인을 자주 해야 하므로 사용자 경험적으로 좋지 않고, 유효 기간을 길게 두면 보안상 탈취 위험에서 벗어날 수 없다.
- 해결법은 유효 기간이 다른 `JWT 토큰` 2개(`Acses Token`과 `Refresh Token`)을 두는 것이다.

## Process

- `Access Token`의 **유효기간은** **짧다**. (ex. 60일([마이크로소프트](https://learn.microsoft.com/en-us/linkedin/shared/authentication/programmatic-refresh-tokens)), 1시간([아마존](https://developer.amazon.com/docs/login-with-amazon/access-token.html)))
- `Refresh Token`의 **유효기간은** **길다**. (ex. 1년 ([마이크로소프트](https://learn.microsoft.com/en-us/linkedin/shared/authentication/programmatic-refresh-tokens)))
- 평소에 API 통신할 때는 Access Token을 사용하고, Refresh Token은 Access Token이 만료되어 갱신될 때만 사용한다.

즉, 통신 과정에서 탈취 당할 위험이 큰 Access Token의 만료 기간을 짧게 두고 Refresh Token으로 주기적으로 재발급 함으로써 피해를 최소화한 것이다.


## 구체적인 서버,클라이언트 통신

---

1. 로그인 인증에 성공한 클라이언트는 `Refresh Token`과 `Access Token` 두 개를 **서버로부터 받는다**.
2. 클라이언트는 `Refresh Token`과 `Access Token`을 **로컬**에 저장해놓는다.
3. 클라이언트는 **헤더**에 Access Token을 넣고 API 통신을 한다. **(Authorization)**
4. 일정 기간이 지나 `Access Token`의 **유효기간이 만료**되었다. Access Token은 이제 유효하지 않으므로 **권한이 없는 사용자**가 된다. 클라이언트로부터 유효기간이 지난 Access Token을 받은 서버는 [401 (Unauthorized)](https://www.rfc-editor.org/rfc/rfc6750#section-6.2.2) 에러 코드로 응답한다.  `401`를 통해 클라이언트는 `invalid_token` (유효기간이 만료되었음)을 알 수 있다.
5. **헤더**에 Access Token 대신 `Refresh Token`을 넣어 **API를 재요청**한다.
6. Refresh Token으로 사용자의 권한을 확인한 서버는 **응답쿼리 헤더**에 **새로운 Access Token**을 넣어 응답한다.
7. 만약 `Refresh Token`도 **만료**되었다면 서버는 동일하게 **401 error code**를 보내고, 클라이언트는 **재로그인**해야한다.
