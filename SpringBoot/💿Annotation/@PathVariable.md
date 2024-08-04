# 1.@PathVariable
    URL 경로에 포함된 변수를 메서드 매개변수로 바인딩할 때 사용하는 애노테이션입니다.
    클라이언트가 요청 URL에서 제공한 값을 메서드의 파라미터로 직접 받아 사용할 수 
    있습니다.


# 2.@PathVariable 기능
## 2-1.URL 경로의 변수 추출
    URL 경로에 포함된 변수를 메서드의 파라미터로 바인딩하여 사용할 수 있습니다.

## 2-2.동적 URL 처리
    URL 패턴을 동적으로 처리하여 다양한 요청에 대응할 수 있습니다.


# 3.@PathVariable 사용 예시

```java
// @PathVariable을 사용하여 URL 경로의 'id' 값을 메서드 파라미터로 받음
    @GetMapping("/user/{id}")
    public String getUserById(@PathVariable("id") Long userId) {
        // 'userId'는 URL에서 추출한 값
        return "User ID: " + userId;
    }
```


```java
 // 여러 PathVariable을 사용하는 예제
    @GetMapping("/user/{userId}/post/{postId}")
    public String getUserPost(@PathVariable("userId") Long userId,
                              @PathVariable("postId") Long postId) {
        // URL 경로에서 추출한 'userId'와 'postId'를 사용
        return "User ID: " + userId + ", Post ID: " + postId;
    }
```

```java
// PathVariable에 기본값을 설정하는 예제 (Spring 4.3 이상)
    @GetMapping("/user/{id}")
    public String getUserById(@PathVariable(value = "id", required = false) Long userId) {
        // 'userId'가 제공되지 않으면 null
        return userId != null ? "User ID: " + userId : "User ID not provided";
    }
```