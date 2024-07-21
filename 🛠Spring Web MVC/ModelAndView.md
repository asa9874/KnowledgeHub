# 1.ModelAndView
    ModelAndView는 Spring Framework에서 사용자의 요청을 처리한 후, 
    컨트롤러가 반환하는 모델 데이터와 뷰 정보를 함께 캡슐화하는 객체입니다.
    ModelAndView는 MVC 패턴에서 모델과 뷰를 한 번에 처리할 수 있도록 도와줍니다.
    (요즘 잘 사용안한다고함)

```java
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.servlet.ModelAndView;

@Controller
public class GreetingController {

    @GetMapping("/greeting")
    public ModelAndView greeting() {
        ModelAndView modelAndView = new ModelAndView();
        modelAndView.setViewName("greeting");  // 뷰 이름 설정
        modelAndView.addObject("message", "Hello, World!");  // 모델 데이터 추가
        
        return modelAndView;
    }
}
```

# 2.ModelAndView 역할
## 2-1.모델 데이터 설정
    컨트롤러가 뷰에 전달할 데이터를 설정할 수 있습니다.
    ModelAndView 객체에 데이터를 추가하면, 해당 데이터는 뷰에서 사용 가능합니다.

## 2-2.뷰 정보 설정
    어떤 뷰를 사용해서 응답을 생성할지 설정합니다.
    뷰 이름을 설정하면, ViewResolver에 의해 실제 뷰로 변환됩니다.
