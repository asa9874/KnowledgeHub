# 1.@RequestParam
    HTTP 요청의 쿼리 파라미터를 메서드 파라미터로 바인딩할 때 사용하는 
    애노테이션입니다.
    URL의 쿼리 문자열 또는 폼 데이터에서 값을 메서드의 파라미터로 쉽게 추출할 수 
    있습니다.

# 2.@RequestParam 기능
## 2-1.쿼리 파라미터 추출
    URL의 쿼리 파라미터를 메서드의 파라미터로 바인딩하여 사용할 수 있습니다.

## 2-2.폼 데이터 처리
    HTML 폼에서 제출된 데이터를 메서드 파라미터로 받아 처리할 수 있습니다.

## 2-3.기본값 설정
    쿼리 파라미터가 제공되지 않을 때 기본값을 설정할 수 있습니다.

## 2-4.필수 여부 설정
    쿼리 파라미터의 필수 여부를 설정할 수 있습니다.


# 3. @RequestParam 사용
```java
// @RequestParam을 사용하여 쿼리 파라미터 'name'을 메서드 파라미터로 받음
    @GetMapping("/greet")
    public String greetUser(@RequestParam("name") String name) {
        return "Hello, " + name + "!";
    }
```


```java
 // 쿼리 파라미터 'name'이 제공되지 않으면 기본값 'Guest'를 사용
    @GetMapping("/greet")
    public String greetUser(@RequestParam(value = "name", defaultValue = "Guest") String name) {
        return "Hello, " + name + "!";
    }
```


```java
// 'name' 파라미터는 필수로 설정 (기본값 false)
    @GetMapping("/greet")
    public String greetUser(@RequestParam(value = "name", required = true) String name) {
        return "Hello, " + name + "!";
    }
```


```java
// 여러 쿼리 파라미터를 사용하는 예제
    @GetMapping("/search")
    public String search(@RequestParam String query, 
                         @RequestParam(defaultValue = "10") int limit) {
        return "Searching for: " + query + " with limit: " + limit;
    }
```