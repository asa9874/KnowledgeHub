# 1.CORS(Cross-Origin Resource Sharing)
    웹 브라우저에서 서버로 요청할 때, 서로 다른 도메인 간의 리소스 공유를 
    허용하거나 제한하기 위한 보안 기능입니다.


# 2.CORS 개념
## 2-1.동일 출처 정책(Same-Origin Policy)
    웹 애플리케이션의 보안을 위해 스크립트가 다른 출처(origin)의 리소스와 
    상호작용하는 것을 제한합니다. 
    (동일 출처는 프로토콜, 도메인, 포트가 모두 같은 경우를 말합니다.)

## 2-2.프리플라이트 요청 (Preflight Request)
    실제 요청 전에 브라우저가 서버로 OPTIONS 메서드를 사용하여 보내는 
    요청입니다. 이 요청을 통해 서버는 실제 요청이 허용되는지 확인할 수 
    있습니다. 주로 PUT, DELETE와 같은 메서드나 사용자 정의 헤더가 포함된 
    요청에서 사용됩니다.

## 2-3.액츄얼 요청 (Actual Request)
    프리플라이트 요청 후, 서버가 CORS 정책에 따라 요청을 허용하면 실제 데이터
    요청이 이루어집니다.

## 2-4.CORS 헤더
    서버는 다양한 CORS 관련 헤더를 사용하여 클라이언트가 요청을 허용할지 
    결정합니다.


# 3.SpringBoot에서 CORS
## 3-1. 컨트롤러 메소드 수준
```java
@RestController
@RequestMapping("/api")
public class MyController {

    // 특정 메서드에 대해 CORS 설정
    @CrossOrigin(origins = "http://example.com")
    @GetMapping("/data")
    public String getData() {
        return "Hello, World!";
    }
}
```

## 3-2. 컨트롤러 클래스 수준
```java
@RestController
@RequestMapping("/api")
@CrossOrigin(origins = "http://example.com")
public class MyController {

    @GetMapping("/data")
    public String getData() {
        return "Hello, World!";
    }
}
```


## 3-3. 글로벌 수준
```java
@Configuration
public class WebConfig {

    @Bean
    public WebMvcConfigurer corsConfigurer() {
        return new WebMvcConfigurer() {
            @Override
            public void addCorsMappings(CorsRegistry registry) {
                registry.addMapping("/api/**")
                        .allowedOrigins("http://example.com")
                        .allowedMethods("GET", "POST", "PUT", "DELETE")
                        .allowedHeaders("*")
                        .allowCredentials(true)
                        .maxAge(3600);
            }
        };
    }
}
```