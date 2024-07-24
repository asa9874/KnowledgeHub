# 1.DAO (Data Access Object)
    소프트웨어 디자인 패턴 중 하나로, 데이터베이스 또는 다른 지속성 메커니즘과의 
    상호 작용을 담당하는 객체를 의미합니다.
    DAO 패턴은 데이터베이스에 대한 접근 로직과 비즈니스 로직을 분리하여 코드의 
    유지보수성을 높이고, 테스트를 용이하게 합니다.

    Spring Data JPA를 사용하면 DAO 인터페이스만 정의하면 되고, 구현 클래스는 자동으로 생성됩니다.
    
# 2.DAO 패턴 구조
## 2-1.DAO 인터페이스
    데이터 접근 메서드의 인터페이스를 정의합니다.
```java
@Repository
public interface UserRepository extends JpaRepository<User, Long> {
    // 기본적인 CRUD 메서드는 JpaRepository가 제공
    // 추가적인 쿼리 메서드는 여기에 정의
    List<User> findByName(String name);
}
```


## 2-2.DAO 구현 클래스
    DAO 인터페이스를 구현하며, 실제 데이터베이스 접근 로직을 포함합니다.
    Spring Data JPA를 사용하면 별도로 구현필요없음

## 2-3.모델 클래스
    데이터베이스 테이블에 매핑되는 엔티티 클래스입니다.


```java
@Entity
public class User {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;
    private String email;

    // getters and setters
}
```
## 2-4.데이터베이스 연결 관리
    데이터베이스 연결을 관리하는 역할을 수행합니다.
