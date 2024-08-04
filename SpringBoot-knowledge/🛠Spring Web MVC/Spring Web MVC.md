# 1.Spring Web MVC
    Spring 프레임워크의 서브 프레임워크로, 웹 애플리케이션을 개발하기 위한
    모델-뷰-컨트롤러(MVC) 패턴을 구현합니다. 
    Spring Web MVC는 웹 애플리케이션의 구성 요소를 체계적으로 분리하고, 
    개발자가 웹 애플리케이션의 비즈니스 로직, 사용자 인터페이스,
    데이터 접근을 각각 독립적으로 개발할 수 있도록 돕습니다.


# 2.MVC
    사용자 인터페이스, 데이터 및 논리 제어를 구현하는데 널리 사용되는 소프트웨어 디자인 패턴,
    애플리케이션을 세 가지 주요 컴포넌트로 분리하여 개발 및 유지보수를 용이하게 하는 아키텍처 패턴이다.
    코드의 응집도는 높이고 결합도는 낮추는 효과를 기대할 수 있다.

![image](https://github.com/user-attachments/assets/c37452f5-6051-4c8b-94de-a22bedcc0e04)





# 3.MVC구성 요소
## 3-1.Model (모델)
- 애플리케이션의 데이터 및 비즈니스 로직을 담당합니다.
- 데이터베이스와의 상호작용, 상태 관리, 비즈니스 규칙 등을 처리합니다.
- 모델은 뷰나 컨트롤러에 대해 알지 못합니다.

```java
public class User {
    private String name;
    private int age;

    // Getter and Setter methods
    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}
```

## 3-2.View (뷰)
- 사용자 인터페이스를 담당합니다.
- 모델의 데이터를 사용자에게 보여주는 역할을 합니다.
- 뷰는 데이터 표시와 관련된 로직만 포함하고 있으며, 비즈니스 로직이나 데이터 처리 로직은 포함하지 않습니다.

```html
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<html>
<head>
    <title>User Details</title>
</head>
<body>
    <h1>User Details</h1>
    <p>Name: ${user.name}</p>
    <p>Age: ${user.age}</p>
</body>
</html>
```
## 3-3.Controller (컨트롤러)
- 사용자 입력을 처리하고, 이를 모델과 뷰로 전달하는 역할을 합니다.
- 사용자의 요청을 받아 모델을 업데이트하고, 업데이트된 모델을 바탕으로 뷰를 다시 렌더링합니다.


```java
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;

@Controller
public class UserController {

    @GetMapping("/user")
    public String getUser(@RequestParam("name") String name, @RequestParam("age") int age, Model model) {
        User user = new User();
        user.setName(name);
        user.setAge(age);
        model.addAttribute("user", user);
        return "user"; // user.jsp로 전달
    }
}
```


# 4. Spring Web MVC의 동작 순서
1. 핸들러 조회:DispatcherServlet이 HandlerMapping을 사용하여 요청 URL에 매핑된 핸들러(컨트롤러)를 조회합니다.
2. 핸들러 어댑터 조회:DispatcherServlet이 해당 핸들러를 실행할 수 있는 HandlerAdapter를 조회합니다.
3. 핸들러 어댑터 실행:DispatcherServlet이 조회한 HandlerAdapter를 실행합니다.
4. 핸들러 실행:HandlerAdapter가 실제 핸들러(컨트롤러)를 실행하여 요청을 처리합니다.
5. ModelAndView 반환:핸들러가 요청을 처리한 결과로 ModelAndView 객체를 반환합니다.
6. viewResolver 호출:DispatcherServlet이 ViewResolver를 사용하여 논리적인 뷰 이름을 물리적인 뷰 객체로 변환합니다.
7. View 반환:ViewResolver가 뷰의 논리 이름을 물리 이름으로 바꾸고, 렌더링 역할을 담당하는 뷰 객체를 반환합니다.
8. 뷰 렌더링:반환된 뷰 객체를 사용하여 최종적으로 사용자에게 응답을 렌더링합니다.
