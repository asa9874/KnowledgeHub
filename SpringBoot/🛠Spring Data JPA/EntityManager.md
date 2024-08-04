# 1.EntityManager
    JPA(Java Persistence API)에서 엔티티의 생명 주기를 관리하고 데이터베이스 작업을 
    수행하는 데 사용되는 주요 인터페이스입니다.
    EntityManager를 통해 데이터베이스와 상호작용하며 엔티티를 저장, 수정, 삭제 및 
    조회할 수 있습니다.

# 2.EntityManager 기능
## 2-1.Persisting Entities
    새로운 엔티티 객체를 데이터베이스에 저장합니다.

## 2-2.Finding Entities
    데이터베이스에서 엔티티 객체를 조회합니다.

## 2-3.Removing Entities
    데이터베이스에서 엔티티 객체를 삭제합니다.

## 2-4.Querying
    JPQL(Java Persistence Query Language) 또는 네이티브 SQL을 사용하여 
    데이터베이스를 쿼리합니다.

## 2-5.Transaction Management
    엔티티 매니저를 통해 트랜잭션을 시작, 커밋 및 롤백합니다.



# 3.EntityManager 사용하기
## 3-1. spring-boot-starter-data-jpa 의존성 추가
```xml
<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-jpa</artifactId>
    </dependency>
    <dependency>
        <groupId>com.h2database</groupId>
        <artifactId>h2</artifactId>
        <scope>runtime</scope>
    </dependency>
</dependencies>
```


## 3-2.EntityManager 사용 서비스 클래스
    EntityManager를 사용하여 사용자 정의 데이터베이스 작업을 수행할 수 있습니다.

```java
@Service
public class UserService {
    
    // EntityManager 주입
    @PersistenceContext
    private EntityManager entityManager;
    
    // 트랜잭션 내에서 실행
    @Transactional
    public User saveUser(User user) {
        entityManager.persist(user); // 새로운 엔티티 저장
        return user;
    }
    
    public User findUserById(Long id) {
        return entityManager.find(User.class, id); // 엔티티 조회
    }
    
    @Transactional
    public void deleteUser(Long id) {
        User user = entityManager.find(User.class, id); // 엔티티 조회
        if (user != null) {
            entityManager.remove(user); // 엔티티 삭제
        }
    }
}
```