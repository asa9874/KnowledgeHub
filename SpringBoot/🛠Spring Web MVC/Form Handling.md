# 1.Form Handling
    Spring Framework에서 Form Handling은 웹 애플리케이션에서 HTML 폼을 처리하는 방법을 말합니다.
    사용자가 입력한 데이터를 서버로 보내고, 서버에서 이를 처리한 후 다시사용자에게 응답을 보낼 수 있습니다.
    Spring Boot는 자동 설정을 통해 대부분의 설정 작업을 간소화하여 빠르게 폼 데이터를 처리할 수 있도록 도와줍니다.

# 2. Spring Boot에서 Fom Handling 하기
1. 폼 객체(Form Object): 폼 데이터를 담을 객체를 정의합니다.
2. 컨트롤러(Controller): 폼 데이터를 처리하는 로직을 구현합니다.
3. 폼 뷰(Form View): HTML 폼을 생성하고, 데이터를 표시합니다.
4. 데이터 바인딩(Data Binding): 폼 데이터를 객체에 바인딩하고 검증합니다.
5. 검증(Validation): 폼 데이터의 유효성을 검사합니다.



## 2-1. 의존성추가
        spring-boot-starter-web 및 spring-boot-starter-thymeleaf 의존성을
        포함한다.
```xml
<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-thymeleaf</artifactId>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-validation</artifactId>
    </dependency>
</dependencies>
```

## 2-2.폼 객체(Form Object)
    폼 데이터를 담을 객체를 정의합니다. 
```java
public class User {

    @NotEmpty(message = "Name is required")
    private String name;

    @NotEmpty(message = "Email is required")
    @Email(message = "Email should be valid")
    private String email;

    // Getters and Setters
    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getEmail() {
        return email;
    }

    public void setEmail(String email) {
        this.email = email;
    }
}
```

## 2-3.컨트롤러(Controller)
    컨트롤러는 폼 데이터를 처리하는 로직을 포함합니다. 

```JAVA
@Controller
public class UserController {

    @GetMapping("/register")
    public String showForm(Model model) {
        model.addAttribute("user", new User());
        return "register";
    }

    @PostMapping("/register")
    public String submitForm(@Valid @ModelAttribute("user") User user, BindingResult result, Model model) {
        if (result.hasErrors()) {
            return "register";
        }
        model.addAttribute("message", "User registered successfully");
        return "success";
    }
}
```

## 2-4.폼 뷰(Form View)
    HTML 폼을 생성하고, 데이터를 표시하는 뷰를 작성합니다.
```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
    <title>Register</title>
</head>
<body>
    <h1>Register</h1>
    <form th:action="@{/register}" th:object="${user}" method="post">
        <label for="name">Name:</label>
        <input type="text" id="name" th:field="*{name}" />
        <div th:if="${#fields.hasErrors('name')}" th:errors="*{name}">Name Error</div>
        <br/>
        <label for="email">Email:</label>
        <input type="email" id="email" th:field="*{email}" />
        <div th:if="${#fields.hasErrors('email')}" th:errors="*{email}">Email Error</div>
        <br/>
        <button type="submit">Submit</button>
    </form>
    <div th:if="${message}">
        <p th:text="${message}"></p>
    </div>
</body>
</html>
```

## 2-5.데이터 바인딩
    데이터 바인딩은 클라이언트로부터 받은 데이터를 Java 객체에 자동으로 
    매핑하는 것을 의미합니다.
    @ModelAttribute와 @RequestBody 애노테이션을 사용하여 이 작업을 
    수행합니다.

## 2-6.검증
    javax.validation 패키지와 함께 제공되는 JSR-303/JSR-380 애노테이션을 
    사용하여 검증을 수행합니다. 일반적인 검증 애노테이션으로는 @NotNull, 
    @NotEmpty, @Email, @Size 등이 있습니다. 검증은 @Valid 또는 @Validated 
    애노테이션을 사용하여 활성화할 수 있습니다.