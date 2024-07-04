<aside>
💡 https//localhost:8080/hello를 URL에 입력했을 때 ‘Hello World’ 출력하는 웹 프로그램

</aside>

```java
package com.example.helloworld;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class HelloWorldApplication {

    public static void main(String[] args) {
        SpringApplication.run(HelloWorldApplication.class, args);
    }

}
```

```java
package com.example.helloworld.controller;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.ResponseBody;

@Controller //HelloController 클래스가 컨트롤러의 기능을 수행함
public class HelloController {
    @GetMapping("/hello") //클라의 요청으로 hello 메서드가 실횅됨
    @ResponseBody //hello 메서드의 출력값 그대로 리턴할 것임을 알려 준다.

    public String hello() {
        return "Hello World";
    }

}

```
