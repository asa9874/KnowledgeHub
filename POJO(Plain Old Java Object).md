# POJO(Plain Old Java Object)
    순수한 자바 오브젝트라는 뜻
    복잡한 엔터프라이즈 자바 빈즈(EJB)와 같은 무거운 컴포넌트나 프레임워크를 피하고,
    순수한 자바 객체로 비즈니스 로직을 구현하는 것을 지향
    
    객체지향적인 원리에 충실하면서, 환경과 기술에 종속되지 않고 
    필요에 따라 재활용될 수 있는 방식으로 설계된 오브젝트

# POJO 특징, 사용이유
- 간단함: 특별한 클래스를 상속받거나 인터페이스를 구현하지 않음.
- 캡슐화: 일반적인 자바 객체처럼 필드, 메서드를 가질 수 있음.
- 독립적(유연성): 특정 프레임워크나 기술에 종속되지 않음(다른 환경으로의 전환이 용이).
- 테스트 용이성: 간단한 객체이므로 유닛 테스트 작성이 쉬움.
- 단순성: 복잡한 상속 구조나 특정 프레임워크에 의존하지 않기 때문에 코드가 단순하고 직관적이다.
- 재사용성: 독립적이기 때문에 여러 프로젝트나 모듈에서 재사용할 수 있다.
- 표준화된 접근:자바의 표준을 따르기 때문에 자바 개발자라면 누구나 쉽게 이해하고 사용할 수 있다.


# POJO 중요성
        특정 기술과 환경에 종속되어 의존하게 된 자바 코드는 가독성이 떨어져 유지보수가 힘들다
        그것은 자바의 객체지향 설계의 장점들을 잃어리는것이다.



# POJO가 적용된코드 vs 적용안된코드

순수한 자바 객체로 특정 프레임워크나 기술에 의존하지않는다.
```java
public class Person {
    private String name;
    private int age;

    // 기본 생성자
    public Person() {}

    // 매개변수 있는 생성자
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // Getter와 Setter 메서드
    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}
```





@Entity 및 @Id와 같은 JPA 어노테이션을 사용하여 특정 프레임워크에 의존하고있다.
```java
import javax.persistence.Entity;
import javax.persistence.Id;

@Entity
public class Person {
    @Id
    private Long id;
    private String name;
    private int age;

    // 기본 생성자
    public Person() {}

    // 매개변수 있는 생성자
    public Person(Long id, String name, int age) {
        this.id = id;
        this.name = name;
        this.age = age;
    }

    // Getter와 Setter 메서드
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

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}
```
