# 1.@ModelAttribute
    Spring MVC에서 요청 매개변수를 모델 객체에 바인딩하거나, 모델에 데이터를 
    추가하는 데 사용되는 애노테이션입니다. 이를 통해 클라이언트로부터 전달된 
    폼 데이터를 쉽게 Java 객체에 매핑할 수 있으며, 모델에 데이터 추가도 
    가능합니다.


# 2.@ModelAttribute의 사용법
## 2-1.객체 바인딩
```java
@PostMapping("/register")
public String submitForm(@ModelAttribute User user) {
    // user 객체에 요청 매개변수가 바인딩됩니다.
    return "result";
}
```
## 2-1.특정 이름으로 모델 객체 바인딩
```java
@PostMapping("/register")
public String submitForm(@ModelAttribute("userForm") User user) {
    // "userForm"이라는 이름으로 user 객체가 모델에 추가됩니다.
    return "result";
}
```
## 2-1.메서드 레벨에서 모델 속성 추가
```java
@Controller
public class UserController {

    @ModelAttribute("user")
    public User getUser() {
        return new User();
    }

    @GetMapping("/register")
    public String showForm() {
        return "register";
    }
}
```


# 3.@ModelAttribute 사용 예
## 3-1.요청 매개변수를 모델 객체에 바인딩
    @ModelAttribute를 사용하여 HTTP 요청 매개변수를 Java 객체에 바인딩할 수 있습니다.
    HTTP 요청에서 전달된 데이터를 User 객체에 자동으로 매핑합니다.
```java
@PostMapping("/register")
    public String submitForm(@ModelAttribute User user, Model model) {
        model.addAttribute("message", "User registered successfully");
        return "success";
    }
```

## 3-2.모델에 데이터 추가
    @ModelAttribute를 메서드 레벨에서 사용하여 컨트롤러가 호출되기 전에 
    모델에 공통 데이터를 추가할 수 있습니다.

    아래 코드에서 @ModelAttribute는 모든 컨트롤러에 공통적으로 사용될 
    globalMessage라는 모델 속성을 추가합니다.
```java
@ControllerAdvice
public class GlobalControllerAdvice {

    @ModelAttribute("globalMessage")
    public String addGlobalMessage() {
        return "This is a global message";
    }
}
```


