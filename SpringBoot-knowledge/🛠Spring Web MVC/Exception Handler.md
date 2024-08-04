# 1.Exception Handler
    애플리케이션 내에서 발생하는 예외를 처리하는 메커니즘을 제공하는 기능입니다.
    주로 @Controller 또는 @RestController 클래스 내부에서 정의되며, 
    특정 예외가 발생했을 때 해당 예외를 처리하는 메서드를 지정할 수 있습니다.
    @ExceptionHandler,@ControllerAdvice 애노테이션을 사용한다.

# 2.Exception Handler 사용예시
## 2-1. @ExceptionHandler
    RuntimeException이 발생하면, handleRuntimeException 메서드가 해당 
    예외를 처리하게 한다.
```java
@RestController
@RequestMapping("/api")
public class MyController {

    @GetMapping("/example")
    public String example() {
        if (true) {
            throw new RuntimeException("This is a runtime exception");
        }
        return "example";
    }

    @ExceptionHandler(RuntimeException.class)
    public ResponseEntity<String> handleRuntimeException(RuntimeException ex) {
        return new ResponseEntity<>("Exception handled: " + ex.getMessage(), HttpStatus.INTERNAL_SERVER_ERROR);
    }
}
```

## 2-2.@ControllerAdvice(글로벌 예외 처리)
    @ControllerAdvice는 애플리케이션 전역에서 발생하는 예외를 처리할 수 있게 
    해줍니다.
    GlobalExceptionHandler 클래스가 애플리케이션 전역에서 발생하는 
    RuntimeException 및 Exception을 처리합니다.
```java
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.ControllerAdvice;
import org.springframework.web.bind.annotation.ExceptionHandler;

@ControllerAdvice
public class GlobalExceptionHandler {

    @ExceptionHandler(RuntimeException.class)
    public ResponseEntity<String> handleRuntimeException(RuntimeException ex) {
        return new ResponseEntity<>("Global Exception handled: " + ex.getMessage(), HttpStatus.INTERNAL_SERVER_ERROR);
    }

    @ExceptionHandler(Exception.class)
    public ResponseEntity<String> handleException(Exception ex) {
        return new ResponseEntity<>("Global Exception handled: " + ex.getMessage(), HttpStatus.BAD_REQUEST);
    }
}
```