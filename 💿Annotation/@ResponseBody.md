# 1.@ResponseBody
    Spring MVC에서 컨트롤러 메서드의 반환 값을 
    HTTP 응답 본문으로 직접 전송할 때 사용하는 애노테이션입니다. 
    이 애노테이션을 사용하면, 메서드가 반환하는 값이 
    뷰 리졸버를 통해 처리되지 않고, 그대로 HTTP 응답 본문으로 전송됩니다.


# 2.@ResponseBody 역할
## 2-1.HTTP 응답 본문 설정
    메서드의 반환 값을 HTTP 응답 본문으로 사용합니다.


    GET 요청에 대해 sayHello 메서드가 호출되며, 이 메서드의 반환 값인 "Hello, World!"가 HTTP 응답 본문으로 전송
```java
@RestController
public class MyController {

    @GetMapping("/hello")
    @ResponseBody
    public String sayHello() {
        return "Hello, World!";
    }
}
```


## 2-2.JSON,XML 포맷으로 응답
    반환되는 객체를 JSON, XML 등으로 직렬화하여 응답 본문으로 전송합니다.


    /user 경로로 들어오는 GET 요청에 대해 getUser 메서드가 호출되며,
    이 메서드의 반환 값인 User 객체가 JSON 형식으로 변환되어 HTTP 응답 본문으로 전송됩니다.
```java
@RestController
public class UserController {

    @GetMapping("/user")
    @ResponseBody
    public User getUser() {
        return new User("John", "Doe");
    }
}
```



## 2-3. RESTful 서비스 구현
    RESTful 웹 서비스에서 자주 사용되며, REST API 응답을 쉽게 구현할 수 있습니다.

    
    @RestController는 @Controller와 @ResponseBody를 결합한 애노테이션으로,
    클래스 내 모든 메서드에 자동으로 @ResponseBody가 적용되도록 합니다.
```java
@RestController
public class ProductController {

    @GetMapping("/product")
    public Product getProduct() {
        return new Product("Laptop", 1500);
    }
}
```

    
