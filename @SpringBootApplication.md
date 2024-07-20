# 1.@SpringBootApplication
    Spring Boot 애플리케이션의 시작 클래스가 자동으로 구성되고
    필요한 컴포넌트들이 자동으로 스캔되어 빈으로 등록됩니다.
    @Configuration
    @EnableAutoConfiguration
    @ComponentScan
    세 가지 애노테이션을 포함합니다

```java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class MySpringBootApplication {

    public static void main(String[] args) {
        SpringApplication.run(MySpringBootApplication.class, args);
    }
}
```
