# 1.@RequestMapping
     Spring MVC에서 사용되는 애노테이션으로, HTTP 요청을 특정 핸들러 메서드와 매핑하기 위해 사용됩니다.
     이를 통해 특정 URL 패턴, HTTP 메서드, 요청 파라미터 등을 기반으로 적절한 메서드를 호출할 수 있습니다.
```java
@Controller
public class MyController {

    @RequestMapping("/hello")
    @ResponseBody
    public String sayHello() {
        return "Hello, World!";
    }
}
```

 # 2.@RequestMapping 역할,예시
 ## 2-1.URL 매핑
     특정 URL 패턴을 핸들러 메서드에 매핑합니다.

     
     /hello 경로로 매핑한다.
```java
@Controller
public class MyController {

    @RequestMapping("/hello")
    @ResponseBody
    public String sayHello() {
        return "Hello, World!";
    }
}
```

 ## 2-2.HTTP 메서드 매핑
     GET, POST, PUT, DELETE 등 특정 HTTP 메서드에 대해 핸들러 메서드를 매핑합니다.

     
     /hello 경로에 대해 GET 요청과 POST 요청을 각각 다른 메서드와 매핑합니다.
```java
@Controller
public class MyController {

    @RequestMapping(value = "/hello", method = RequestMethod.GET)
    @ResponseBody
    public String handleGetRequest() {
        return "Handling GET request";
    }

    @RequestMapping(value = "/hello", method = RequestMethod.POST)
    @ResponseBody
    public String handlePostRequest() {
        return "Handling POST request";
    }
}
```
 ## 2-3.파라미터 매핑
     특정 요청 파라미터가 있는 경우에만 핸들러 메서드를 호출합니다.


     name 파라미터가 있는 경우와 없는 경우를 각각 다른 메서드와 매핑합니다.
```java
@Controller
public class MyController {

    @RequestMapping(value = "/greet", params = "name")
    @ResponseBody
    public String greetUser(@RequestParam("name") String name) {
        return "Hello, " + name;
    }

    @RequestMapping(value = "/greet", params = "!name")
    @ResponseBody
    public String greetAnonymous() {
        return "Hello, Anonymous";
    }
}
```
 ## 2-4.헤더 매핑
     특정 요청 헤더가 있는 경우에만 핸들러 메서드를 호출합니다.
```java
@Controller
public class MyController {

    @RequestMapping(value = "/headerTest", headers = "X-Custom-Header=foo")
    @ResponseBody
    public String handleHeader(@RequestHeader("X-Custom-Header") String headerValue) {
        return "Header value is " + headerValue;
    }
}
```

     
