# 1.Handler Adapter
    Spring MVC의 내부 메커니즘의 일부로, 
    컨트롤러 클래스에서 직접 코드로 사용하는것은아니다.
    컨트롤러는 HandlerAdapter의 사용을 신경 쓸 필요 없이 요청과 응답 처리를 위한 비즈니스 로직을 구현한다.
    
    Spring Web MVC 프레임워크에서 요청을 실제 핸들러(컨트롤러)
    로 전달하여 처리하는 역할을 담당하는 인터페이스이며
    DispatcherServlet은 요청을 처리하기 위해 핸들러를 찾고, 
    이를 실행할 적절한 HandlerAdapter를 사용한다.

# 2.Handler Adapter역할
## 2-1.핸들러 실행
    HandlerAdapter는 HandlerMapping이 찾아낸 핸들러를
    실제로 실행하여 클라이언트 요청을 처리합니다.


## 2-2.호환성 제공
- 다양한 종류의 핸들러를 처리할 수 있도록 여러 종류의 HandlerAdapter가 존재합니다.
- 예: RequestMappingHandlerAdapter, SimpleControllerHandlerAdapter, HttpRequestHandlerAdapter 등.




# 3.Handler Adapter 구현체
## 3-1.RequestMappingHandlerAdapter
    Spring MVC의 기본 HandlerAdapter
    개발자는 직접 HandlerAdapter를 사용하지 않고, 
    Spring MVC의 프레임워크가 이를 자동으로 처리
    @RequestMapping, @GetMapping, @PostMapping 등으로 정의된 핸들러 메소드를 처리합니다.
    
    
    예)
    RequestMappingHandlerAdapter가 ApiController의 
    getGreeting 및 postGreeting 메소드를 처리
```java
@Controller
@RequestMapping("/api")
public class ApiController {

    @GetMapping("/greeting")
    @ResponseBody
    public String getGreeting() {
        return "Hello, World!";
    }

    @PostMapping("/greeting")
    @ResponseBody
    public String postGreeting() {
        return "Posted Greeting!";
    }
}
```

## 3-2.SimpleControllerHandlerAdapter
    Spring MVC의 초기 버전에서 주로 사용
    Controller 인터페이스를 구현한 클래스를 처리

```java
import org.springframework.web.servlet.ModelAndView;
import org.springframework.web.servlet.mvc.Controller;

import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

public class MyController implements Controller {

    @Override
    public ModelAndView handleRequest(HttpServletRequest request, HttpServletResponse response) throws Exception {
        ModelAndView mav = new ModelAndView("viewName");
        mav.addObject("message", "Hello, World!");
        return mav;
    }
}
```













