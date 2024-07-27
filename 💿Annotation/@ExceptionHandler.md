# 1.@ExceptionHandler
    예외를 처리하기 위해 사용되는 애노테이션입니다. 특정 예외가 발생했을 때, 
    이를 처리하는 메서드를 정의할 수 있게 해줍니다. 

# 2. 사용예시
## 2-1.특정 컨트롤러 내에서 예외 처리
```java
@RestController
@RequestMapping("/api")
public class MyController {

    @GetMapping("/data")
    public String getData() {
        // 특정 조건에서 예외 발생
        throw new DataNotFoundException("Data not found");
    }

    // DataNotFoundException 예외 처리 메서드
    @ExceptionHandler(DataNotFoundException.class)
    @ResponseStatus(HttpStatus.NOT_FOUND)
    public String handleDataNotFoundException(DataNotFoundException ex, Model model) {
        model.addAttribute("errorMessage", ex.getMessage()); // 예외 메시지를 모델에 추가
        return "error/404"; // 404 에러 페이지로 이동
    }
}
```


## 2-2. 전역 예외 처리
```java
// 전역 예외 처리를 위한 클래스
@ControllerAdvice
public class GlobalExceptionHandler {

    // DataNotFoundException 예외 처리 메서드
    @ExceptionHandler(DataNotFoundException.class)
    @ResponseStatus(HttpStatus.NOT_FOUND)
    public String handleDataNotFoundException(DataNotFoundException ex, Model model) {
        model.addAttribute("errorMessage", ex.getMessage()); // 예외 메시지를 모델에 추가
        return "error/404"; // 404 에러 페이지로 이동
    }

    // 모든 예외 처리 메서드
    @ExceptionHandler(Exception.class)
    @ResponseStatus(HttpStatus.INTERNAL_SERVER_ERROR)
    public String handleException(Exception ex, Model model) {
        model.addAttribute("errorMessage", ex.getMessage()); // 예외 메시지를 모델에 추가
        return "error/500"; // 500 에러 페이지로 이동
    }
}
```
