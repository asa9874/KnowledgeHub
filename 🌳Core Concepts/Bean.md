# 1.Bean
    Spring IoC 컨테이너에 의해 관리되는 객체
    빈은 스프링 애플리케이션의 핵심 구성 요소로, 
    애플리케이션의 다양한 부분에서 재사용되고, 관리됩니다.
    
    Spring Boot는 자동 설정, 간편한 구성 및 스프링의 강력한 
    빈 관리 기능을 통해 애플리케이션 개발을 간소화합니다.
    
    @Service, @Controller, @Model, @Repository와 같은 애노테이션을 사용하여
    정의된 클래스들은 모두 빈(Bean)으로 등록합니다.


# 2.Bean 예시
## 2-1.서비스 계층의 빈
    @Service 을사용하여 비즈니스 로직을 처리하는 서비스 계층의 빈을 정의합니다.
```java
import org.springframework.stereotype.Service;

@Service
public class MyService {
    // 비즈니스 로직
}
```

## 2-2.컨트롤러 계층의 빈
    @Controller를 사용하여 웹 요청을 처리하고, 모델을 업데이트하고, 
    뷰를 반환하는 컨트롤러 계층의 빈을 정의합니다. MVC 패턴에서 컨트롤러 역할을 수행합니다.

```java
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;

@Controller
@RequestMapping("/example")
public class MyController {

    @GetMapping("/greeting")
    public String greeting() {
        return "greetingView";
    }
}
```

## 2-3.데이터 접근 계층의 빈
    @Repository을 사용하여데이터 접근 계층의 빈을 정의합니다. 
    데이터베이스와의 상호작용을 담당하며, 예외를 데이터 접근 관련 예외로 변환합니다.

```java
import org.springframework.stereotype.Repository;

@Repository
public class MyRepository {
    // 데이터 접근 로직
}
```

## 2-4.일반적인 빈
    @Component을 사용하여 일반적인 빈을 정의합니다. 
    특정 역할에 구애받지 않고 모든 종류의 빈을 정의할 때 사용합니다.


