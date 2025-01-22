## Oauth 2.0

<aside>

**🚀 Oauth 2.0(Open Authorization 2.0)!**

</aside>

> **인증 및 권한 부여**를 위한 **업계 표준 프로토콜**이다.
> 
- 사용자가 특정 웹사이트에 로그인하기 위해 다른 웹사이트(구글, 페이스북 등)의 계정을 사용하도록 하는 방식이다.
- 구글, 페이스북, 트위터와 같은 다양한 플랫폼의 특정한 사용자 데이터에 접근하기 위해 제3자 클라이언트(우리의 서비스)가 사용자의 **접근 권한을 위임(Delegated Authorization)**받을 수 있는 표준 프로토콜

## Oauth 용어

---

> **Resource Owner**
> 
- 리소스 소유자
    - 우리의 서비스를 이용하면서, 구글, 페이스북 등의 플랫폼에서 리소스를 소유하고 있는 사용자
- 즉 해당 플랫폼에서 리소스를 소유하고 있는 사용자를 의미한다.
    - 우리의 웹 서비스를 이용하는 유저

> **Authorization Server**
> 
- Authorization Server는 Resource Owner를 인증하고, 우리가 개발한 웹 서비스에게 Access Token을 발급해주는 서버
- 외부 플랫폼 리소스에 접근할 수 있는지 인증을 하는 서버

> **Resource Server**
> 
- 구글,페이스북, 카카오와 같이 보호되는 리소스를 가지는 서버

> **Client**
> 
- Resource Server의 자원을 이용하고자 하는 서비스
- Client란 Resource Owner 를 대신해 Authorization Server & Resource Server 에 접근하는 주체
즉 우리가 개발하려는 서비스이다.

<aside>

우리가 개발하려는 서비스를 Client라고 정의한 이유는 우리 서비스가 Authorization Server & Resource Server 입장에서 클라이언트이기 때문이다.

</aside>

## Oauth 2.0 동작 메커니즘

---

> **`OAuth 2.0`** 서비스를 이용하기전에 **Client**를 **Resource** **Server** 에 등록해야 한다.
이때, **Redirect** **URI**를 등록해야한다.
> 
- **Redirect** **URI**는 사용자가 **`OAuth 2.0`** 서비스에서 인증을 마치고 (예를 들어 구글 로그인 페이지에서 로그인을 마쳤을 때) 사용자를 리디렉션시킬 위치이다.
- 등록과정을 마치면, **Client ID**와 **Client Secret**를 얻을 수 있다. 발급된 **Client ID**와 **Client Secret**은 액세스 토큰을 획득하는데 사용된다. 이때, **Client ID**는 공개되어도 상관없지만, **Client Secret**은 절대 유출되어서는 안된다. 심각한 보안사고로 이어질 수 있다.

https://hudi.blog/static/7dced69214d91d7f1f0892720b1b5e1b/9afce/oauth2.0-process.png

### **1 ~ 2. 로그인 요청**

---

> Resource Owner가 우리 서비스의 '구글로 로그인하기' 등의 버튼을 클릭해 로그인을 요청한다.
Client는 OAuth 프로세스를 시작하기 위해 사용자의 브라우저를 Authorization Server로 보내야한다.
> 
- Client는 이때 Authorization URL에 response_type, client_id, redirect_uri, scope 등의 매개변수를 쿼리 스트링으로 포함하여 보낸다.

ex) 어떤 OAuth 2.0 서비스의 Authorization URL이 **`https://authorization-server.com/auth`** Client는 아래와 같은 URL을 빌드한다.

```
https://authorization-server.com/auth?response_type=code
&client_id=29352735982374239857
&redirect_uri=https://example-app.com/callback
&scope=create+delete
```

**Authorization Server에게 보낼 매개변수**

---

- **response_type**: OAuth 2.0 인증 과정에서 클라이언트가 요청하는 응답 유형을 지정, 이 값이 **`code`**로 설정되면, 인증 서버는 인증이 성공한 후 **Authorization Code**를 클라이언트에게 반환
- **client_id**: 웹 서비스를 Resource Server에 등록했을 때 발급받은 Client ID
- **redirect_uri**: 웹 서비스를 Resource Server에 등록했을 때 등록한 redirect URI
- **scope**: Client가 부여받은 리소스 접근 권한을 의미

### **3 ~ 4. 로그인 페이지 제공 및 ID/PW 입력**

---

> Client 로부터 Authorization URL로 이동된 Resource Owner는 제공된 로그인 페이지에서 ID/PW을 입력하여 인증
> 

### **5 ~ 6. Authorization Code 발급, Redirect URI로 리디렉트**

---

> Authorization URL에서 인증이 성공했다면, Authorization server는 기존에 설정한 Redirect URL에 **Authorization Code** 를 포함하여 사용자를 리다이렉션 시킨다.
> 
- **Authorization code**란 리소스 접근을 위한 Access Token을 획득하기 위해 사용하는 임시 코드이며, 수명은 매우 짧다.

### **7 ~ 8. Authorization Code와 Access Token 발급**

---

> Client는 다시 Authorization Server에 Authorization Code를 전달하고, Access Token을 발급받는다.
> 
- Client는 자신이 발급받은 Resource Owner의 Access Token을 데이터베이스에 저장하고, 이후 Resource Server에서 Resource Owner의 리소스에 접근하기 위해 Access Token을 사용합니다
- Access Token은 유출되어서는 안된다.

### **9. 로그인 성공**

---

> 위 과정을 성공적으로 마치면 Client는 Resource Owner에게 로그인이 성공하였음을 알린다.
> 

### **10 ~ 13. Access Token으로 리소스 접근**

---

> 이후 Resource Owner가 Resource Server의 리소스가 필요한 기능을 Client에 요청한다
> 
- Client는 위 과정에서 발급받고 저장해둔 Resource Owner의 Access Token을 사용하여 제한된 리소스에 접근하고, Resource Owner에게 자신의 서비스를 제공한다.

## **OAuth 2.0 Scope 란?**

---

> scope란 Client가 사용 가능한 Resource 접근 범위를 제한하는 것
> 
- 예를 들어 구글 플렛폼을 Resource Server로 사용할 때, 사용자의 연락처를 받아오고 싶다면, scope에 연락처 scope 문자열을 포함하여 서버에 요청하면 된다.
- 이러한 방식으로 발급된 Access Token은 Scope 정보를 가지고 있어 권한을 제한한다.

## Oauth 2.0에서 FE와 BE

---

> Client가 인증을 위해 Authorization URL을 통해 Authorization Server로 이동할 때 해당 URL은 누가 생성할까?
> 
- 백엔드 프론트엔드 어느곳에서나 생성해도 정상적인 동작에 지장은 없지만, Client ID , Scope와 같은 정보들은 백엔드 쪽에서 가지고 있기 때문에 응집도 측면에서 백엔드에서 생성하는것이 좋다. (역시 백엔드가 짱이다)
- 이렇게 생성한 Authorization URL을 프론트엔드가 가져와 사용자를 Authorization Server로 리다이렉 시킨다.
- 인증을 모두 마치면 지정한 Redirect URL로 돌아옵니다. 보통 Redirect URL 은 프론트쪽으로 설정합니다. (Authorization Code와 함께 온다.)
    - Authorization Code를 받은 프론트엔드는 다시 해당 Code를 백엔드 API를 통해 백엔드 쪽으로 보내고 백엔드는 Authorization Code, Client ID, Client Secret 등으로 Access Token을 받는다.

<aside>

**정리**

- Authorization URL 은 Client 백엔드가 생성한다.
- Client 프론트단은 해당 URL을 리다이렉트 시켜 브라우저가 인증을 가능하게 하도록 한다.
- 인증 결과로 받은 Authorization Code는 Client 프론트단에서 받는다.
- 프론트단은 Authorization Code를 백단으로 다시 보낸다.
- 백단에서 Authorization Code와 더불어 다양한 정보로 Authorization Server 로부터 Access Token을 발급 받는다.
</aside>

### 참고자료

https://velog.io/@choidongkuen/OAuth02-%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%BC%EA%B9%8C

https://hudi.blog/oauth-2.0/ ← 강추

https://engineerinsight.tistory.com/163#%F0%9F%92%8B%C2%A0OAuth%202.0%EC%9D%98%20%EA%B3%BC%EC%A0%95-1
