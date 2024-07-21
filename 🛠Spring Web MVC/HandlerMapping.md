# 1.HandlerMapping 
    Spring Web MVC 프레임워크에서 중요한 인터페이스로, 
    요청을 적절한 핸들러(컨트롤러)로 매핑하는 역할을 담당하는 컴포넌트입니다.
    HandlerMapping 자체는 Spring MVC의 프레임워크에서 제공되는 인터페이스이며, 
    개발자가 직접 구현할 필요는 없습니다.
    
    클라이언트의 요청 URL을 적절한 핸들러(컨트롤러)와 매핑하는 역할
    (request의 URL과 매칭되는 handler를 선택하는 역할)

    RequestMappingHandlerMapping이 가장 현대적이고 많이 사용되는 방식

# 2.HandlerMapping 주요 구현체
## 2-1.BeanNameUrlHandlerMapping
    URL과 빈 이름을 가지고 Controller 맵핑
    빈 이름을 URL 패턴으로 사용하는 핸들러 매핑입니다. 
    빈 이름이 요청 URL과 일치하는 핸들러를찾습니다.
    빈 이름이 /hello이면, /hello로 들어오는 요청을 해당 빈이 처리하게된다.

```java
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;

@Controller("/hello")
public class HelloController {

    @RequestMapping
    public String handleRequest() {
        return "hello"; // View name
    }
}
```

### XML 파일
```XML
<bean id="urlMapping" class="org.springframework.web.servlet.handler.BeanNameUrlHandlerMapping"/>

<bean id="/hello" class="com.example.HelloController"/>
```

## 2-2.SimpleUrlHandlerMapping
    URL과 Controller을 직접 맵핑
    정적 URL 패턴을 기반으로 핸들러를 매핑합니다. 
    주로 XML 설정 파일을 통해 매핑을 설정합니다.
    
```java
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;

@Controller
public class HelloController {

    @RequestMapping("/hello")
    public String handleRequest() {
        return "hello"; // View name
    }
}
```
### XML 파일
```XML
<bean id="urlMapping" class="org.springframework.web.servlet.handler.SimpleUrlHandlerMapping">
    <property name="mappings">
        <value>
            /hello=helloController
        </value>
    </property>
</bean>

<bean id="helloController" class="com.example.HelloController"/>
```

## 2-3.ControllerClassNameHandlerMapping
    URL과 Controller 명을 일정한 규칙으로 맵핑
    클래스 이름을 URL 패턴으로 사용하는 핸들러 매핑입니다. 
    컨트롤러 클래스 이름을 기반으로 요청 URL과 매핑합니다.
```java
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;

@Controller
public class HelloWorldController {

    @RequestMapping
    public String handleRequest() {
        return "hello"; // View name
    }
}
```
### XML 파일
```XML
<bean id="urlMapping" class="org.springframework.web.servlet.mvc.support.ControllerClassNameHandlerMapping"/>

<bean id="helloWorldController" class="com.example.HelloWorldController"/>
```


## 2-4.RequestMappingHandlerMapping 
    @RequestMapping 애노테이션을 기반으로 URL 패턴과 핸들러 메소드를 매핑합니다.
    가장 많이 사용되는 매핑 구현체입니다.

```java
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.ResponseBody;

@Controller
@RequestMapping("/api")
public class ApiController {

    @GetMapping("/greeting")
    @ResponseBody
    public String getGreeting() {
        return "Hello, World!";
    }

    @PostMapping("/greeting")
    @ResponseBody
    public String postGreeting() {
        return "Posted Greeting!";
    }
}
```
### Config 파일
```java
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.web.servlet.config.annotation.EnableWebMvc;
import org.springframework.web.servlet.config.annotation.WebMvcConfigurer;
import org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerMapping;

@Configuration
@EnableWebMvc
public class WebConfig implements WebMvcConfigurer {

    @Bean
    public RequestMappingHandlerMapping requestMappingHandlerMapping() {
        RequestMappingHandlerMapping mapping = new RequestMappingHandlerMapping();
        // 추가 설정 가능
        return mapping;
    }
}
```

