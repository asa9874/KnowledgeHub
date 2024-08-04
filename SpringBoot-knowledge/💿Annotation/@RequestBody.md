# 1.@RequestBody
    Spring MVC에서 HTTP 요청 본문(body)을 Java 객체로 변환할 때 
    사용하는 애노테이션입니다.주로 JSON 형식의 요청 데이터를 처리할 때 
    사용됩니다.
    Spring Boot 애플리케이션에서 RESTful 웹 서비스와 같은 기능을 간단하게 
    구현할 수 있습니다.


# 2.@RequestBody 사용 예시
## 2-1.객체 생성
```java
@RestController
public class UserController {

    @PostMapping("/users")
    public User createUser(@RequestBody User user) {
        // 클라이언트로부터 전달된 JSON을 User 객체로 변환하여 처리
        return user;
    }
}
```

## 2-2.JSON 데이터와 검증
```java
@RestController
public class ProductController {

    @PostMapping("/products")
    public ResponseEntity<Product> addProduct(@Valid @RequestBody Product product) {
        // @Valid 애노테이션으로 검증된 JSON을 Product 객체로 변환하여 처리
        return ResponseEntity.ok(product);
    }
}
```

## 2-3.복잡한 JSON 객체 처리
```java
@RestController
public class OrderController {

    @PostMapping("/orders")
    public OrderResponse createOrder(@RequestBody OrderRequest orderRequest) {
        // 클라이언트로부터 전달된 JSON을 OrderRequest 객체로 변환하여 처리
        // 여기서는 단순히 변환된 객체를 반환하는 예제입니다.
        return new OrderResponse("Order received", orderRequest);
    }
}
```