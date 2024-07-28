# 1.spring-boot-starter-data-jpa
    Spring Boot에서 JPA (Java Persistence API)를 쉽게 설정하고 사용할 수 있도록 도와주는 스타터 의존성
    JPA 관련 라이브러리와 자동 설정을 포함하고 있어, JPA를 사용한 데이터 액세스와 관리를 간편하게 할 수 있다.



# 2.spring-boot-starter-data-jpa 기능
## 2-1.자동 설정
    JPA 관련 설정을 자동으로 구성합니다. 
    데이터베이스 연결, JPA 구현체 설정, 엔티티 매니저, 
    Hibernate의 스키마 생성 및 갱신 설정 등이 자동으로 설정됩니다.

## 2-2.Spring Data JPA 통합
    Spring Data JPA를 포함하여, 
    JPA를 더욱 효율적으로 사용할 수 있도록 돕는 추가 기능을 제공합니다.

## 2-3.내장 JPA 구현체
    Hibernate를 기본 JPA 구현체로 포함하고 있으며, 
    이를 통해 데이터베이스와의 상호작용을 처리합니다

## 2-4.리포지토리 지원
    Spring Data JPA의 JpaRepository 인터페이스를 통해 리포지토리를 자동으로 생성하고,
    기본적인 CRUD 작업 및 쿼리 메서드를 지원합니다.


## 2-5.스키마 생성 및 갱신
    spring.jpa.hibernate.ddl-auto 속성을 통해 데이터베이스 스키마의 자동 생성 및 갱신 설정을 지원합니다.


## 2-6.엔티티 클래스 자동 탐색
    @Entity 애노테이션이 붙은 클래스들을 자동으로 탐색하여 데이터베이스 테이블과 매핑합니다.


# 3.spring-boot-starter-data-jpa 구성요소
## 3-1.스타터 의존성
    프로젝트의 빌드 파일에 해당 의존성을 추가
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>
```

## 3-2.Spring Boot 애플리케이션
    @SpringBootApplication 애노테이션이 붙은 메인 클래스를 정의하여 애플리케이션을 시작합니다.
```java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class MyApplication {
    public static void main(String[] args) {
        SpringApplication.run(MyApplication.class, args);
    }
}
```


## 3-3.데이터베이스 설정
    데이터베이스 연결 정보를 application.properties 또는 application.yml 파일에 설정합니다.
```
spring.datasource.url=jdbc:mysql://localhost:3306/mydb
spring.datasource.username=root
spring.datasource.password=password
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

## 3-4.엔티티(모델) 클래스
    데이터베이스 테이블과 매핑되는 자바 클래스를 정의 
```java
import javax.persistence.Entity;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;
import javax.persistence.Id;

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

## 3-5.리포지토리(Repository) 인터페이스
    데이터베이스 작업을 처리하기 위한 리포지토리 인터페이스를 정의합니다.
```java
import org.springframework.data.jpa.repository.JpaRepository;

public interface UserRepository extends JpaRepository<User, Long> {
    User findByName(String name);
}
```

## 3-6.컨트롤러(Controller)
    JPA 리포지토리를 사용하는 컨트롤러를 정의하여 클라이언트 요청을 처리합니다.

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class UserController {

    @Autowired
    private UserRepository userRepository;

    @PostMapping("/users")
    public User createUser(@RequestBody User user) {
        return userRepository.save(user);
    }

    @GetMapping("/users/{name}")
    public User getUserByName(@PathVariable String name) {
        return userRepository.findByName(name);
    }
}
```



# 4.포함 애노테이션
- @Entity: JPA 엔티티를 정의.
- @Table: 엔티티와 매핑할 데이터베이스 테이블을 지정.
- @Id: 엔티티의 기본 키를 지정.
- @GeneratedValue: 기본 키의 생성 전략을 지정.
- @Column: 엔티티의 필드와 데이터베이스 컬럼을 매핑.
- @OneToOne: 일대일 관계를 매핑.
- @OneToMany: 일대다 관계를 매핑.
- @ManyToOne: 다대일 관계를 매핑.
- @ManyToMany: 다대다 관계를 매핑.
- @JoinColumn: 관계를 매핑할 때 사용할 외래 키 컬럼을 지정.
- @JoinTable: 다대다 관계를 매핑할 조인 테이블을 지정.
- @Query: JPQL 또는 네이티브 쿼리를 정의.
- @NamedQuery: 이름이 지정된 쿼리를 정의.
- @Modifying: 데이터 변경 쿼리를 정의.
- @Transactional: 메서드 또는 클래스에 트랜잭션 설정을 적용.
- @EnableJpaRepositories: JPA 리포지토리를 활성화.
- @EntityListeners: 엔티티의 라이프사이클 이벤트 리스너를 지정.
- @Version: 낙관적 잠금을 위한 버전 필드를 지정.
- @Temporal: 날짜/시간 타입을 매핑.