# 1.@ControllerAdvice
    전역적으로 예외를 처리하고, 컨트롤러에 대한 전역 설정을 제공하는데 
    사용됩니다. 이 애노테이션을 사용하면 특정 컨트롤러뿐만 아니라 애플리케이션 
    전체에서 발생하는 예외를 처리할 수 있습니다.


# 2. 기능
## 2-1.전역 예외 처리
    애플리케이션 전체에서 발생하는 예외를 한 곳에서 처리할 수 있습니다.
```java
@ControllerAdvice // 전역 예외 처리를 담당하는 클래스
public class GlobalExceptionHandler {

    @ExceptionHandler(DataNotFoundException.class) // DataNotFoundException 예외 처리
    @ResponseStatus(HttpStatus.NOT_FOUND) // HTTP 상태 코드를 404로 설정
    public String handleDataNotFoundException(DataNotFoundException ex, Model model) {
        model.addAttribute("errorMessage", ex.getMessage()); // 모델에 예외 메시지를 추가
        return "error/404"; // 에러 페이지로 이동
    }

    @ExceptionHandler(Exception.class) // 모든 예외 처리
    @ResponseStatus(HttpStatus.INTERNAL_SERVER_ERROR) // HTTP 상태 코드를 500으로 설정
    public String handleException(Exception ex, Model model) {
        model.addAttribute("errorMessage", ex.getMessage()); // 모델에 예외 메시지를 추가
        return "error/500"; // 에러 페이지로 이동
    }
}
```

## 2-2.모델 객체 설정
    모든 컨트롤러에서 공유할 수 있는 모델 객체를 설정할 수 있습니다.
```java
// 전역 모델 객체 설정을 위한 클래스
@ControllerAdvice
public class GlobalModelAttribute {

    // 모든 뷰에 공유할 모델 속성 설정 메서드
    @ModelAttribute("globalMessage")
    public String globalMessage() {
        return "This is a global message available in all controllers";
    }
}
```



## 2-3.전역 데이터 바인딩 설정
    모든 컨트롤러에 대해 데이터 바인딩 관련 설정을 전역적으로 적용할 수
    있습니다.

```java
// 전역 데이터 바인딩 설정을 위한 클래스
@ControllerAdvice
public class GlobalBindingInitializer implements WebBindingInitializer {

    // WebDataBinder 초기화 메서드
    @InitBinder
    public void initBinder(WebDataBinder binder) {
        // 날짜 형식을 전역적으로 설정
        SimpleDateFormat dateFormat = new SimpleDateFormat("yyyy-MM-dd");
        binder.registerCustomEditor(Date.class, new CustomDateEditor(dateFormat, false));
    }

    @Override
    public void initBinder(WebDataBinder binder, WebRequest request) {
        initBinder(binder); // initBinder 메서드 호출
    }
}
```
