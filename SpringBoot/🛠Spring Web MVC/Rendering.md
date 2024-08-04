# 1.Rendering
    뷰(View)를 클라이언트에게 전달하기 위해 최종적으로
    HTML이나 다른 형태의 응답을 생성하는 과정
    웹 애플리케이션에서 컨트롤러가 반환한 모델 데이터를 
    실제 사용자에게 보여질 형태로 변환하는 단계


# 2.Spring Boot Rendering 과정
## 2-1.컨트롤러에서 요청 처리 및 모델 데이터 반환
    컨트롤러는 클라이언트의 요청을 처리하고, 뷰 이름과 함께 모델 데이터를 반환
    Spring Boot에서는 @Controller 또는 @RestController 애노테이션을 사용하여 컨트롤러를 정의
```java
@Controller
public class MyController {

    @GetMapping("/greeting")
    public String greeting(Model model) {
        model.addAttribute("message", "Hello, Spring Boot!");
        return "greeting"; // 뷰 이름
    }
}
```

## 2-2.뷰 리졸버(View Resolver) 호출
    DispatcherServlet은 컨트롤러가 반환한 뷰 이름을 바탕으로 뷰 리졸버(ViewResolver)를 호출


## 2-3.뷰 객체 생성
    뷰 리졸버는 뷰 이름을 바탕으로 뷰 객체를 생성합니다. 
    이 객체는 JSP, Thymeleaf, FreeMarker 등으로 작성된 템플릿을 처리합니다.


## 2-4.모델 데이터와 뷰 렌더링
    생성된 뷰 객체는 모델 데이터를 사용하여 최종 HTML을 생성합니다.
    예를 들어, Thymeleaf 템플릿 엔진은 모델 데이터를 템플릿에 삽입하여 HTML을 생성합니다.
    
```java
<!-- src/main/resources/templates/greeting.html -->
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
    <title>Greeting</title>
</head>
<body>
    <h1 th:text="${message}">Hello, Spring Boot!</h1>
</body>
</html>
```



## 2-5.클라이언트 응답
    렌더링된 HTML이 클라이언트에게 응답으로 전달됩니다.
    클라이언트는 이를 브라우저에 표시하여 최종 결과를 확인합니다.

