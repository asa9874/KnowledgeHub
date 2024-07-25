# 1.Interceptor
    Spring 프레임워크에서 HTTP 요청과 응답을 가로채고, 처리하기 전에 특정 작업을
    수행할 수 있는 메커니즘입니다. 주로 공통 로직을 구현하거나, 인증 및 인가, 
    로깅, 성능 측정 등의 용도로 사용됩니다.

# 2.Interceptor 기능
## 2-1.공통 작업 수행
    모든 요청에 대해 공통적으로 수행해야 하는 작업을 처리할 수 있습니다. 
    (인증/인가 체크, 요청 로깅, 공통 헤더 설정 등)

## 2-2.전처리/후처리 로직
    요청이 컨트롤러에 도달하기 전과 후에 특정 작업을 수행할 수 있습니다.
    (요청 전 유효성 검사, 응답 후 로깅 등)

## 2-3.제어 흐름 관리
    특정 조건에 따라 요청 처리를 중단하거나, 특정 로직을 추가로 실행할 수 
    있습니다.


# 3.Interceptor 구현법
## 3-1.spring-boot-starter-web 의존성 추가
```xml
<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
</dependencies>
```

## 3-2.Interceptor 구현
    HandlerInterceptor 인터페이스를 구현하여 인터셉터를 정의합니다.
    세 가지 주요 메서드가 있습니다

```java
@Component
public class CustomInterceptor implements HandlerInterceptor {

    @Override
    public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception {
        // 요청이 컨트롤러에 도달하기 전에 실행
        System.out.println("Pre Handle method is Calling");
        return true; // true이면 다음 인터셉터나 컨트롤러로 요청을 전달
    }

    @Override
    public void postHandle(HttpServletRequest request, HttpServletResponse response, Object handler, ModelAndView modelAndView) throws Exception {
        // 컨트롤러가 실행된 후, 뷰가 렌더링되기 전에 실행
        System.out.println("Post Handle method is Calling");
    }

    @Override
    public void afterCompletion(HttpServletRequest request, HttpServletResponse response, Object handler, Exception ex) throws Exception {
        // 뷰가 렌더링된 후에 실행
        System.out.println("Request and Response is completed");
    }
}
```


## 3-3.Interceptor 등록
    Spring 설정 클래스에서 인터셉터를 등록합니다.

```java
@Configuration
public class WebConfig implements WebMvcConfigurer {

    @Autowired
    private CustomInterceptor customInterceptor;

    @Override
    public void addInterceptors(InterceptorRegistry registry) {
        registry.addInterceptor(customInterceptor)
                .addPathPatterns("/api/**") // 특정 경로 패턴에만 인터셉터 적용
                .excludePathPatterns("/api/login"); // 특정 경로는 인터셉터 제외
    }
}
```


## 3-4.Spring Boot 애플리케이션 클래스
```java
@SpringBootApplication
public class InterceptorExampleApplication {

    public static void main(String[] args) {
        SpringApplication.run(InterceptorExampleApplication.class, args);
    }
}
```