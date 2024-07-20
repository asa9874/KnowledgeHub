# 1.Controller
    MVC (Model-View-Controller) 패턴에서 사용자의 요청을 처리하고, 
    모델 데이터를 업데이트하며, 뷰를 선택하여 최종적으로 응답을 생성하는 역할을 담당하는 구성 요소입니다. 

# 2.Controller 역할
## 2-1.요청 매핑
    특정 URL 패턴에 대한 HTTP 요청을 메서드와 매핑합니다.
    @RequestMapping, @GetMapping, @PostMapping 등의 애노테이션을
    사용하여 요청을 처리할 메서드를 정의합니다.

## 2-2.비즈니스 로직 호출
    서비스 계층의 비즈니스 로직을 호출하여 필요한 처리를 수행합니다.
    일반적으로 서비스 클래스와 통합하여 데이터를 처리하고 변환합니다.

## 2-3.모델 데이터 준비
    처리된 데이터를 모델에 추가하여 뷰에서 사용 가능하도록 합니다.
    Model 객체를 통해 뷰에 전달할 데이터를 설정합니다.

## 2-4.뷰 선택
    요청에 대한 응답으로 렌더링할 뷰를 선택합니다.
    일반적으로 뷰 이름을 반환하거나, @ResponseBody를 사용하여 직접 응답 본문을 작성합니다.


# 3.Controller 예제
## 3-1.@Controller
```java
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;

@Controller
public class GreetingController {

    @GetMapping("/greeting")
    public String greeting(@RequestParam(name="name", required=false, defaultValue="World") String name, Model model) {
        model.addAttribute("name", name);
        return "greeting";
    }
}
```


## 3-2.@RestController
```java
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class GreetingRestController {

    @GetMapping("/api/greeting")
    public Greeting greeting(@RequestParam(name="name", required=false, defaultValue="World") String name) {
        return new Greeting("Hello, " + name);
    }
    
    public static class Greeting {
        private String message;

        public Greeting(String message) {
            this.message = message;
        }

        public String getMessage() {
            return message;
        }
    }
}
```
