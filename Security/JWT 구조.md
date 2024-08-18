# JWT 구조

<aside>
🚀 JWT 구조

</aside>

- JWT는 .을 구분자로 나누어지는 세 가지 문자열의 조합이다.
- .을 기준으로 좌측부터 Header, Payload, Signature를 의미한다.

## Header(헤더)

---

<aside>
🚀 **Header는 두 가지 정보를 담고 있다.**

</aside>

1. **typ**
    - 토큰의 타입을 지정합니다. (ex: JWT)
2. **alg**
    - 해싱 알고리즘을 지정합니다. (보통 `HMAC SHA256` 혹은 `RSA` 가 사용된다.)
    - 이 알고리즘은 토큰을 검증하는 signature부분에서 사용된다.

## Payload

---

<aside>
🚀 **Payload에는 토큰에 담을 정보인 ‘Claim’이 들어있다.**

</aside>

- 서버와 클라이언트가 주고 받는 시스템에서 실제로 **사용될 정보에 대한 내용**이 담겨있다.
- **Key-value** 형식으로 이루어진 한 쌍의 정보를 **Claim**이라고 한다.

### Payload의 분류

<aside>
🚀 **Payload는 정해진 데이터 타입은 없지만 3가지로 나눌 수 있다.**

</aside>

### Registed(등록된) Claims

- iss ( issuer ; 발행자 )
- exp ( expireation time ; 만료 시간 )
- sub ( subject ; 제목 )
- iat ( issued At ; 발행 시간 )
- jti( JWT ID)

### Public(공개) claims

- 사용자가 정의할 수 있는 클레임 공개용 정보 전달을 위해 사용한다.
- 공개 클레임들은 충돌이 방지된 이름을 가지고 있어야 합니다. 충돌을 방지하기 위해서는, 클레임 이름을 [URI](https://en.wikipedia.org/wiki/Uniform_resource_identifier) 형식으로 짓는다.

```
{
    "https://velopert.com/jwt_claims/is_admin": true
}
```

### Private(비공개) claims

- 해당하는 당사자들 간에 정보를 공유하기 위해 만들어진 사용자 지정 클레임 외부에 공개되도 상관없지만 해당 유저를 특정할 수 있는 정보들을 담는다.
- 공개 클레임과는 달리 이름이 중복되어 충돌이 될 수 있으니 사용할 때에 유의해야 한다.

```
{
    "username": "velopert"
}
```

## Signature

---

<aside>
🚀 **Header + Payload** 와 서버가 갖고 있는 유일한 **key값**을 합친 것을 Header에서 알고리즘으로 암호화한 값이다.

</aside>

- Header와 Payload는 단순히 **Base64URL**로 인코딩 되어있어 누구나 쉽게 디코딩 할 수 있지만,
- Signature의 key가 없으면 디코딩 할 수 없다. (보안상 안전하다.)

> **앞서 언급한 것처럼**
> 
- Header에서 선언한 알고리즘에 따라 key는 개인 키가 될 수도 있고 비밀 키가 될 수도 있다.
    - 개인 키로 서명했다면 공개 키로 유효성 검사를 할 수 있고
    - 비밀 키로 서명했다면 비밀 키를 가지고 있는 사람만이 암호화 복호화, 유효성 검사를 할 수 있다.
