# 1.@Component
    Spring 프레임워크에서 사용되는 어노테이션으로, 개발자가 만든 클래스를 
    Spring의 빈(Bean)으로 등록하는 데 사용됩니다. 이 어노테이션을 사용하면 
    Spring이 해당 클래스를 자동으로 인식하고, 애플리케이션 컨텍스트 에 빈으로 
    등록합니다.
    그러나 대부분의 경우, Spring Boot에서는 좀 더 구체적인 역할을 표현하기 
    위해 @Controller, @Service, @Repository와 같은 어노테이션을 사용합니다.

```java
@Component
public class MyComponent {

    public void doSomething() {
        System.out.println("Doing something...");
    }
}
```
# 2.기능
## 2-1.빈 등록
    @Component가 붙은 클래스를 Spring 컨테이너에 빈으로 등록합니다.

## 2-2.자동 스캔
    Spring의 클래스패스 스캔 기능을 통해 @Component 어노테이션이 붙은 
    클래스를 자동으로 검색하여 빈으로 등록합니다.


## 2-3.의존성 주입
    다른 빈에서 @Autowired를 통해 @Component 빈을 주입받을 수 있습니다.
```java
@Autowired
    public MyService(MyComponent myComponent) {
        this.myComponent = myComponent;
    }
```
