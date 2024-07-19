# 1.JPA(Java Persistence API)
    Java EE 와 Java SE 플랫폼을 위한 자바 표준 ORM API이다
    JPA는 자바 객체와 관계형 데이터베이스 간의 매핑을 제공해준다.
    데이터베이스의 데이터를 자바 객체로 쉽게 변환하고 
    반대로 자바 객체를 데이터베이스에 저장할 수 있게 해준다.
    JPA는 데이터베이스 작업을 추상화하여, 개발자가 직접 SQL을 작성하지 않아도 되도록 돕는다.

# 2.JPA 특징
## 2-1.객체-관계 매핑 (ORM)
    JPA는 자바 객체와 데이터베이스 테이블 간의 매핑을 정의합니다.
    이를 통해 자바 객체를 데이터베이스의 레코드로 저장하고, 
    반대로 데이터베이스의 레코드를 자바 객체로 변환할 수 있습니다.

## 2-2.엔티티 클래스
    JPA를 사용하면 데이터베이스 테이블에 매핑되는 엔티티 클래스를 정의할 수 있습니다.
    각 엔티티 클래스는 데이터베이스의 테이블과 매핑되며, 
    클래스의 각 필드는 테이블의 컬럼과 매핑됩니다.
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

    private String email;
    private String name;

    // getters and setters
}
```

## 2-3.JPQL
    객체를 대상으로 하는 쿼리 언어입니다. 
    SQL과 유사한 문법을 가지며, 엔티티 객체를 대상으로 쿼리를 작성합니다.
    
```java
String jpql = "SELECT u FROM User u WHERE u.email = :email";
TypedQuery<User> query = em.createQuery(jpql, User.class);
query.setParameter("email", "example@example.com");
List<User> users = query.getResultList();
```


## 2-4.EntityManager
    JPA의 핵심 인터페이스로, 엔티티를 데이터베이스에 저장하고,
    쿼리를 수행하며, 트랜잭션을 관리합니다.
```java
EntityManagerFactory emf = Persistence.createEntityManagerFactory("my-persistence-unit");
EntityManager em = emf.createEntityManager();
```



