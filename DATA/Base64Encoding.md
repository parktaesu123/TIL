<aside>
🚀 **Base64Encoding(인코딩)이란?**

</aside>

- **Binary 데이터**를 텍스트로 바꾸는 **인코딩**이다.
- char-set에 영향 받지 않는 **ASCII 문자열**로만 되어 있는 텍스트로 바꾸는 일을 한다.

- 인코딩 방식
    - Binary 데이터를 **6bit**씩 자른 후 해당되는 문자열을 **ASCII 값**으로 치환해준다.
    - 6bit이기 때문에 2의 6제곱, 64개의 글자가 있으면 어떤 데이터든 표현할 수 있다.
    - Base64는 3byte씩 쪼개서 6bit씩 **인코딩**을 합니다. 여기서 3byte가 안되는 경우에는 padding 문자열로 채운다.

<aside>
🚀 **왜 쓰냐??**

</aside>

- **Base64를 사용하는 가장 큰 이유는 Binary 데이터를 텍스트 기반 규격으로 다룰 수 있기 때문이다.**
- JSON과 같은 문자열 기반 데이터 안에 이미지 파일등을 Web에서 필요로 할때 Base64로 인코딩하면 UTF-8과 호환 가능한 문자열을 얻을 수 있다.

### 참고 자료

https://velog.io/@jungmyeong96/Base64-Encoding-vs-Base64Url-Encoding
