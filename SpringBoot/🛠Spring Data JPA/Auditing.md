# 1.Auditing
    소프트웨어 애플리케이션에서 데이터의 생성, 수정, 삭제와 같은 중요한 
    이벤트를 기록하는 프로세스를 말합니다. 이를 통해 애플리케이션에서 어떤 
    변화가 있었는지 추적하고 기록할 수 있으며, 데이터의 변경 이력을 관리하고 
    보안을 강화하는 데 중요한 역할을 합니다.


# 2.Spring Boot에서 Auditing
    엔터티의 생성 및 수정 정보를 자동으로 기록하고 관리하는 기능을 제공합니다.
    누가, 언제 데이터를 생성하거나 수정했는지 추적할 수 있습니다.

# 3. 사용법
## 3-1.Auditing 활성화
    @EnableJpaAuditing 애노테이션을 추가하여 JPA Auditing을 활성화합니다.
```java
@SpringBootApplication
@EnableJpaAuditing // JPA 감사(Auditing) 기능 활성화
public class MyApplication {
    public static void main(String[] args) {
        SpringApplication.run(MyApplication.class, args);
    }
}
```

## 3-2.엔터티 클래스에 Auditing 필드 추가

```java
@Entity
@EntityListeners(AuditingEntityListener.class) // Auditing 엔터티 리스너 추가
public class MyEntity {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @CreatedDate // 생성 날짜 자동 설정
    private LocalDateTime createdDate;

    @LastModifiedDate // 수정 날짜 자동 설정
    private LocalDateTime lastModifiedDate;

    @CreatedBy // 생성자 자동 설정
    private String createdBy;

    @LastModifiedBy // 수정자 자동 설정
    private String lastModifiedBy;

    // Getters and Setters
}
```

## 3-3.AuditorAware 구현
    누가 데이터를 생성하고 수정했는지 기록하려면 AuditorAware 인터페이스를 
    구현해야 합니다.
```java
@Configuration
@EnableJpaAuditing // JPA Auditing 활성화
public class AuditingConfig {

    @Bean
    public AuditorAware<String> auditorProvider() {
        return new AuditorAwareImpl();
    }
}

class AuditorAwareImpl implements AuditorAware<String> {

    @Override
    public Optional<String> getCurrentAuditor() {
        // 실제로는 SecurityContext 또는 Session에서 현재 사용자 정보를 가져와야 합니다.
        // 여기서는 예시로 "admin"을 반환합니다.
        return Optional.of("admin");
    }
}
```