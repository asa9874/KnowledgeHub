# 1.Criteria API
    Criteria API는 JPA (Java Persistence API)의 일부로, 동적 쿼리를 타입
    안전하게 작성할 수 있는 API입니다.
    SQL 쿼리 대신 자바 객체를 사용하여 쿼리를 구성하고 실행할 수 있어 코드의 
    안전성과 유지보수성을 높여줍니다.
    spring-boot-starter-data-jpa에 포함되어있다.

# 2.Criteria API 사용이유
## 2-1.타입 안전성
    쿼리를 컴파일 타임에 검증할 수 있어, 런타임 에러를 줄일 수 있습니다.

## 2-2.동적 쿼리
    복잡한 쿼리 조건을 동적으로 구성할 수 있어, 유연한 쿼리 작성이 가능합니다.

## 2-3.가독성
    쿼리의 가독성을 높일 수 있으며, 자바 코드로 쿼리를 작성하기 때문에 코드 
    유지보수가 쉬워집니다.

# 3. 구성요소
1. CriteriaBuilder 
    쿼리 생성의 시작점을 제공하는 객체입니다. EntityManager에서 얻을 수 있으며,
    CriteriaQuery, CriteriaUpdate, CriteriaDelete 객체를 생성하는 데 
    사용됩니다.

2. CriteriaQuery
    쿼리의 구조를 정의하는 객체입니다. CriteriaBuilder에서 생성되며, 
    쿼리의 선택 항목, 조건, 정렬 등을 설정합니다.

3. Root
    쿼리의 루트 엔티티를 정의합니다. 
    쿼리의 대상이 되는 엔티티를 지정합니다.

4. Predicate
    쿼리의 조건을 정의하는 객체입니다. 
    CriteriaBuilder를 통해 생성되며, Root와 함께 사용하여 필터링 조건을 
    추가합니다.

5. TypedQuery
    최종 쿼리 객체로, CriteriaQuery를 통해 쿼리를 구성하고, EntityManager에서
    실행하여 결과를 얻습니다.

# 4. Springboot에서 사용법
    EntityManager를 사용하여 Criteria API를 활용할 수 있습니다. 
    EntityManager는 @Autowired를 통해 주입받을 수 있습니다.

```java
@Service
public class UserService {

    @Autowired
    private EntityManager entityManager;

    public List<User> findUsersByName(String name) {
        CriteriaBuilder criteriaBuilder = entityManager.getCriteriaBuilder();
        CriteriaQuery<User> criteriaQuery = criteriaBuilder.createQuery(User.class);
        Root<User> root = criteriaQuery.from(User.class);
        criteriaQuery.select(root).where(criteriaBuilder.equal(root.get("name"), name));

        TypedQuery<User> query = entityManager.createQuery(criteriaQuery);
        return query.getResultList();
    }
}
```


