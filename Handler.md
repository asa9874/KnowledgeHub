# 1.Handler
    Handler는 클라이언트의 요청을 처리하는 객체를 의미
    일반적으로 컨트롤러(Controller)가 Handler 역할을 수행
    Handler는 클라이언트의 요청을 받아 비즈니스 로직을 수행하고,
    그 결과를 생성하여 응답을 반환하는 역할


# 2.Handler 역할
## 2-1.요청 처리
- 클라이언트로부터의 HTTP 요청을 수신합니다.
- 요청 데이터를 검증하고 비즈니스 로직을 수행합니다.

```java
@Controller
@RequestMapping("/greeting")
public class GreetingController {
```



## 2-2.응답 생성
- 처리 결과를 바탕으로 응답을 생성합니다.
- 응답 데이터는 뷰 템플릿으로 전달되어 클라이언트에게 렌더링됩니다.

```java
@GetMapping("/hello")
@ResponseBody
public String handleRequest() {
    return "Hello, World!";
}

@GetMapping("/helloView")
public ModelAndView handleRequestWithView() {
    ModelAndView mav = new ModelAndView("helloView");
    mav.addObject("message", "Hello, World!");
    return mav;
}
```


# 3. Handler 예시
## 3-1.@Controller 클래스
```java
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.ResponseBody;

@Controller
@RequestMapping("/greeting")
public class GreetingController {

    @GetMapping
    @ResponseBody
    public String handleRequest() {
        return "Hello, World!";
    }
}
```
