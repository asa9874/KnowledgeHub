# 1.@Bean
    메서드 수준에서 사용되어 스프링 IoC 컨테이너가 관리할 빈을 정의합니다.
    @Configuration 클래스 내에 선언된 @Bean 메서드는 빈 정의를 제공하며,
    해당 메서드의 반환 객체가 스프링 컨테이너에 의해 빈으로 등록됩니다.

```java
@Configuration
public class AppConfig {

    @Bean
    public MyService myService() {
        return new MyServiceImpl();
    }
}

```
### 빈이름을 name속성으로 지정할수도 있습니다.
```java
@Configuration
public class AppConfig {

    @Bean(name = "customService")
    public MyService myService() {
        return new MyServiceImpl();
    }
}
```
