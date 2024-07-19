# 1.Spring Data JPA
    JPA (Java Persistence API)를 사용하는 데이터 액세스를 쉽게 관리할 수 있도록 도와주는 라이브러리
    JPA의 복잡한 설정과 구현을 단순화하며, 개발자가 데이터베이스 작업을
    더 간편하게 수행할 수 있도록 다양한 기능을 제공합니다.


# 2.Spring Data JPA 기능
## 2-1.리포지토리 인터페이스 자동 생성
    개발자는 리포지토리 인터페이스를 정의하기만 하면 Spring Data JPA가 필요한 구현을 자동으로 생성합니다.
    JpaRepository, CrudRepository, PagingAndSortingRepository 등의 인터페이스를 통해
    CRUD 및 페이지네이션, 정렬 작업을 자동으로 처리할 수 있습니다.


## 2-2.쿼리 메서드
    메서드 이름을 기반으로 자동으로 쿼리를 생성합니다.
```java
public interface UserRepository extends JpaRepository<User, Long> {
    User findByEmail(String email);
    List<User> findByLastName(String lastName);
}
```


## 2-3.JPQL 및 네이티브 쿼리
    JPQL (Java Persistence Query Language)을 사용하여 복잡한 쿼리를 작성할 수 있으며,
    네이티브 SQL 쿼리도 지원합니다.
```java
@Query("SELECT u FROM User u WHERE u.email = ?1")
User findByEmail(String email);

@Query(value = "SELECT * FROM users WHERE email = ?1", nativeQuery = true)
User findByEmailNative(String email);
```

## 2-4.페이징 및 정렬
    페이지네이션과 정렬 기능을 제공하여, 
    대량의 데이터를 페이지 단위로 처리할 수 있습니다.
```java
Page<User> findByLastName(String lastName, Pageable pageable);
```

## 2-5.커스터마이징 및 확장
    사용자 정의 리포지토리 인터페이스와 구현체를 추가하여 
    복잡한 데이터 액세스 로직을 처리할 수 있습니다.
    
```java
public interface UserRepositoryCustom {
    List<User> findUsersWithCustomQuery();
}

public class UserRepositoryImpl implements UserRepositoryCustom {
    @PersistenceContext
    private EntityManager entityManager;

    @Override
    public List<User> findUsersWithCustomQuery() {
        // Custom JPQL or SQL query implementation
    }
}
```






