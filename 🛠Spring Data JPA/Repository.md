# 1.Repository
    Spring Boot에서의 Repository는 데이터 액세스 계층을 구성하는 핵심 요소로, 
    주로 Spring Data JPA를 사용하여 구현됩니다.
    
    Repository는 데이터베이스와의 상호작용을 단순화하고, CRUD (Create, Read, 
    Update, Delete) 작업을 쉽게 수행할 수 있도록 도와줍니다.

    Spring Boot는 대부분의 설정을 자동으로 처리합니다. application.properties
    파일에 데이터베이스 설정만 추가하면 됩니다.

```java
package com.example.demo;

import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.stereotype.Repository;

@Repository
public interface UserRepository extends JpaRepository<User, Long> {
    // 추가적인 쿼리 메서드 정의 가능
    User findByEmail(String email);
}
```

# 2.Spring Data JPA Repository 특징
    Spring Data JPA는 JpaRepository 인터페이스를 제공하여, 기본적인 데이터 
    접근 기능을 자동으로 구현합니다. 개발자는 이 인터페이스를 확장하여 
    리포지토리를 정의하면 됩니다.

## 2-1.자동 CRUD 기능
    JpaRepository를 확장하면 기본적인 CRUD 기능이 자동으로 제공됩니다.

## 2-2.쿼리 메서드
    메서드 이름으로 쿼리를 생성할 수 있으며, 복잡한 쿼리는 @Query 애노테이션을
    사용하여 정의할 수 있습니다.

## 2-3.페이징 및 정렬
    페이징과 정렬 기능을 쉽게 구현할 수 있습니다.

## 2-4.트랜잭션 관리
    리포지토리 메서드는 자동으로 트랜잭션을 처리합니다.

