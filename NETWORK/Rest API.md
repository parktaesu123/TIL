## Rest API

<aside>
🚀 Rest API란?

</aside>

- Rest를 기반으로 만들어진 API / Rest의 원리를 따르는 API
- REST API를 올바르게 설계하기 위해서는 지켜야 하는 몇가지 규칙이 있다.

## Rest


- **REST(Representational State Transfer)**의 약자로 `자원(Resource)`을 이름으로 구분하여 해당 `자원(Resource)`의 상태를 주고받는 모든 것을 의미합니다.

> **HTTP URI(Uniform Resource Identifier)**를 통해 `자원(Resource)`을 명시하고
**HTTP Method**(`POST`, `GET`, `PUT`, `DELETE`, `PATCH` 등)를 통해
해당 자원(`URI`)에 대한 **CRUD Operation**을 적용하는 것을 의미합니다.
> 

### REST 구성 요소

---

1. **자원(Resource) : `HTTP URI`**
2. **자원에 대한 행위 : `HTTP Method`**
3. **자원에 대한 행위의 내용 : `HTTP Message Pay Load`**

### REST 특징

---

1. **Server-Client**(서버-클라이언트 구조)
2. **Stateless**(무상태)
3. **Cacheable**(캐시 처리 가능)
4. **Layered System**(계층화)
5. **Uniform Interface**(인터페이스 일관성)

## Rest API 설계 예시


1. **URI는 동사보다는 명사를, 대문자보다는 소문자를 사용하여야 한다.**

```
Bad EX) http://taesupark123.com/BE/

Good EX) http://taesupark123.com/be/  
```

1. **마지막에 슬래시 (/)를 포함하지 않는다.**

```
Bad EX) http://taesupark123.com/dsm/  

Good EX) http://taesupark123.com/dsm  
```

1. **언더바 대신 하이폰을 사용한다.**

```
Bad EX) http://taesupark123.com/be_engineer

Good EX) http://taesupark123.com/be-engineer  
```

1. **파일확장자는 URI에 포함하지 않는다.**

```
Bad EX) http://taesupark123.com/dog.jpg
  
Good EX) http://taesupark123.com/dog  
```

1. **행위를 포함하지 않는다.**

```
Bad EX http://taesupark123.com/delete-comment/1  

Good EX http://taesupark123.com/comment/1  
```

### 참고자료

[https://khj93.tistory.com/entry/네트워크-REST-API란-REST-RESTful이란](https://khj93.tistory.com/entry/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-REST-API%EB%9E%80-REST-RESTful%EC%9D%B4%EB%9E%80)
