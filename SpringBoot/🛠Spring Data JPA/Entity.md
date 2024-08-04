# 1.Entity
    Java Persistence API(JPA)에서 데이터베이스 테이블에 매핑되는 클래스
    엔티티 클래스는 데이터베이스 테이블의 각 행(row)을 나타내며, 
    클래스의 각 필드는 테이블의 컬럼(column)에 대응합니다.


# 2.Entity 특징
## 2-1.영속성 컨텍스트
    엔티티 객체는 영속성 컨텍스트에 의해 관리됩니다.
    엔티티 객체의 상태 변화를 추적하고 데이터베이스와의 동기화를 처리합니다.


## 2-2.JPA 애노테이션
    엔티티 클래스는 @Entity 애노테이션으로 표시되며, 
    각 필드는 @Id, @Column, @GeneratedValue 등의 JPA 애노테이션으로 매핑됩니다.

## 2-3.ORM(Object-Relational Mapping)
    엔티티 클래스는 객체와 관계형 데이터베이스 간의 매핑을 제공합니다.

```java
package com.example.demo;

import javax.persistence.Entity;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;
import javax.persistence.Id;
import javax.persistence.Table;

@Entity
@Table(name = "users") // 데이터베이스 테이블 이름 지정
public class User {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY) // 기본 키 생성을 데이터베이스에 위임
    private Long id;

    private String name;

    private String email;

    // Getters and Setters
    public Long getId() {
        return id;
    }

    public void setId(Long id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getEmail() {
        return email;
    }

    public void setEmail(String email) {
        this.email = email;
    }
}
```