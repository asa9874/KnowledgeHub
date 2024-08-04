# 1.JTA(Java Transaction API)
    JTA (Java Transaction API)는 분산 트랜잭션을 관리하기 위한 표준 API입니다.
    여러 자원(예: 데이터베이스, 메시지 큐 등)을 포함하는 트랜잭션을 관리하는 데 
    사용됩니다.

# 2.JTA(Java Transaction API) 특징
## 2-1.분산 트랜잭션 관리
    JTA는 단일 자원에서뿐만 아니라 여러 자원에 걸쳐 트랜잭션을 관리할 수 
    있습니다.

## 2-2.트랜잭션 매니저
    JTA는 트랜잭션 매니저를 사용하여 트랜잭션을 시작하고 커밋하거나 롤백합니다.

## 2-3.자원 관리
    JTA는 자원 관리자를 통해 트랜잭션이 여러 자원에 걸쳐 일관되게 수행되도록 
    보장합니다.


# 3.SpringBoot에서 JTA사용법
    Spring Boot는 기본적으로 JPA와 같은 라이브러리를 통해 트랜잭션 관리를
    자동으로 처리하지만, JTA를 사용하면 더 복잡한 분산 트랜잭션을 처리할 수 
    있습니다.

## 3-1. 의존성추가(Atomikos)
     Spring의 JTA 통합 라이브러리중 대표적인 JTA 구현체로는 Atomikos와 Bitronix가 있습니다.
```xml
<dependency>
    <groupId>com.atomikos</groupId>
    <artifactId>transactions-jta</artifactId>
    <version>4.0.6</version>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>
```

## 3-2.JTA 트랜잭션 매니저 설정
    JTA를 사용할 때는 JTA 트랜잭션 매니저를 설정해야 합니다. 
    이 설정은 보통 @Configuration 클래스에서 수행됩니다.
```java
@Configuration
@EnableTransactionManagement
public class JtaConfiguration {

    @Bean
    public UserTransactionManager userTransactionManager() {
        UserTransactionManager userTransactionManager = new UserTransactionManager();
        userTransactionManager.init();
        return userTransactionManager;
    }

    @Bean
    public UserTransactionImp userTransactionImp() {
        UserTransactionImp userTransactionImp = new UserTransactionImp();
        userTransactionImp.setTransactionTimeout(300);
        return userTransactionImp;
    }

    @Bean
    public UserTransactionManager transactionManager() {
        return new UserTransactionManager();
    }

    @Bean
    public TransactionManager transactionManager(UserTransactionManager userTransactionManager) {
        return userTransactionManager;
    }
}
```


## 3-3. JTA 트랜잭션 사용
    일반적인 Spring @Transactional과 동일하지만, 
    JTA 트랜잭션 매니저를 사용하기 때문에 분산 트랜잭션을 지원합니다.
```java
@Service
public class UserService {

    @Autowired
    private UserRepository userRepository;

    @Transactional
    public void createUser(User user) {
        userRepository.save(user);
        // 다른 자원에 대한 작업 수행
    }
}
```