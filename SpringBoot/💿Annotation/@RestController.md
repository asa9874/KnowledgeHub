# 1.@RestController
    Spring Framework에서 RESTful 웹 서비스의 컨트롤러를
    쉽게 만들 수 있도록 제공되는 애노테이션입니다.
    
    @Controller와 @ResponseBody를 결합한 형태로, 클래스 레벨에서 사용하면 
    해당 클래스의 모든 핸들러 메서드가 HTTP 응답 본문을 직접 전송하도록 설정됩니다.


# 2.@RestController 역할
## 2-1.RESTful 웹 서비스 컨트롤러
    RESTful API를 구현할 때 사용

## 2-2.자동 JSON 변환
    메서드의 반환 값을 JSON 형식으로 직렬화하여 HTTP 응답 본문으로 전송


    메서드의 반환 값인 User 객체가 JSON 형식으로 변환되어 HTTP 응답 본문으로 전송됩니다.
```java
@RestController
@RequestMapping("/api")
public class UserController {

    @GetMapping("/user")
    public User getUser() {
        return new User("John", "Doe");
    }
}
```
