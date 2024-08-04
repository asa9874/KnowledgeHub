# 1.@Valid
    Spring MVC와 Spring Boot에서 객체 검증을 수행할 때 사용되는 
    애노테이션입니다. 
    Java Bean Validation API(Bean Validation)를 통해 검증됩니다. 
    검증 실패 시, Spring은 자동으로 적절한 오류 메시지를 생성하여 클라이언트에 
    반환합니다.

# 2.@Valid 용도
1. 데이터 검증: 클라이언트로부터 받은 데이터가 유효한지 확인합니다.
2. 자동 오류 처리: 검증 오류가 발생하면, Spring은 400 Bad Request 응답을 자동으로 반환합니다.
3. 유효성 메시지: 검증 실패 시 사용자에게 피드백을 제공하기 위한 메시지를 설정할 수 있습니다.


# 3.@Valid 사용예시
## 3-1.컨트롤러에서 검증 사용
    @Valid 애노테이션을 사용하여 요청 본문에 포함된 데이터를 검증합니다. 
    검증 오류가 발생하면, Spring은 자동으로 400 Bad Request 응답을 반환합니다.
```java
@PostMapping("/users")
    public ResponseEntity<String> createUser(@Valid @RequestBody User user, BindingResult result) {
        if (result.hasErrors()) {
            // 검증 오류가 있을 경우 처리 (여기서는 간단하게 오류 메시지를 반환)
            return ResponseEntity.status(HttpStatus.BAD_REQUEST).body("Validation failed: " + result.getAllErrors());
        }
        // 검증된 User 객체를 처리합니다.
        return ResponseEntity.ok("User created successfully");
    }
```


## 3-2.컨트롤러에서 HTML 폼 데이터 검증
    폼 데이터를 검증할 때도 @Valid를 사용할 수 있습니다.
    HTML 폼에서 입력된 데이터를 객체에 바인딩하고 검증합니다.

```java
 @PostMapping("/register")
    public String submitForm(@Valid @ModelAttribute("user") User user, BindingResult result, Model model) {
        if (result.hasErrors()) {
            return "register";  // 검증 오류가 있는 경우, 폼을 다시 보여줍니다.
        }
        model.addAttribute("message", "User registered successfully");
        return "success";
    }
```