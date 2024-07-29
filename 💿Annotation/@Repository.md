# 1.@Repository
    Spring Boot 애플리케이션에서 데이터 액세스 계층 클래스에 사용되는 
    어노테이션입니다.

```java
@Repository
public interface UserRepository extends JpaRepository<User, Long> {
    // 사용자 정의 쿼리 메서드 정의 가능
}
```
# 2.기능
## 2-1.DAO 표시
    이 어노테이션을 통해 해당 클래스가 데이터 액세스 계층을 담당하는 DAO 
    클래스임을 명시합니다.

## 2-2.예외 변환
    Spring의 예외 변환 메커니즘을 통해 데이터베이스 접근 중 발생하는 예외를 
    Spring의 DataAccessException으로 변환합니다.


## 2-3.컴포넌트 스캔
    @Component 어노테이션과 같이 Spring이 클래스패스를 스캔할 때 @Repository 
    어노테이션이 붙은 클래스를 자동으로 빈으로 등록합니다.

