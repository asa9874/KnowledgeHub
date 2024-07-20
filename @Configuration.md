# 1.@Configuration
    @Bean이 정의되어있는 클래스에서 사용되는 어노테이션
    하나 이상의 @Bean 메서드를 선언하고 스프링 IoC 컨테이너에 의해
    빈 정의를 생성 및 서비스 요청을 처리할 수 있음을 나타냅니다.
    XML 기반 설정을 대체하는 자바 기반 구성 클래스를 정의할 때 사용됩니다.

# 2.@Configuration 역할
## 2-1.빈 정의 제공
    @Bean 애노테이션이 달린 메서드를 통해 빈을 정의하고, 스프링 컨테이너에 등록합니다.

```java
@Configuration
public class AppConfig {

    @Bean
    public MyService myService() {
        return new MyServiceImpl();
    }
}
```
## 2-2.자바 기반 구성
    XML 설정 파일을 사용하지 않고, 자바 코드로 구성 설정을 정의할 수 있습니다.


