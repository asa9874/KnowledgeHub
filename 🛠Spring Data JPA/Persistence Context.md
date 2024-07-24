# 1.Persistence Context
    Persistence Context는 JPA(Java Persistence API)에서 엔티티
    객체들을 관리하는 환경을 의미합니다. 
    엔티티 객체의 생명주기와 데이터베이스 간의 동기화를 책임지는
    중요한 개념입니다.

    Spring Boot에서는 대부분의 설정이 자동으로 처리되기 때문에 
    개발자가 별도로 Persistence Context에 대해 신경 쓸 필요가 거의 
    없습니다.
    
# 2.주요 개념
## 2-1.엔티티 관리
    Persistence Context는 엔티티 객체의 상태를 추적하고 관리합니다.
    엔티티 객체는 Persistence Context에 의해 관리될 때 영속성 상태
    (persistent state)로 간주됩니다.

## 2-2.1차 캐시
    Persistence Context는 1차 캐시로서 작동하여, 데이터베이스에서 조회된 
    엔티티 객체들을 캐시하고, 동일한 트랜잭션 내에서는 같은 객체를 
    반환합니다.

## 2-3.변경 감지
    Persistence Context는 관리하는 엔티티 객체의 상태 변화를 감지하고,
    트랜잭션이 커밋될 때 변경된 내용을 자동으로 데이터베이스에 반영합니다.

## 2-4.동일성 보장
    동일한 Persistence Context 내에서는 같은 엔티티 객체의 동일성을 
    보장합니다. 즉, 같은 엔티티를 조회하면 동일한 객체가 반환됩니다.



# 3.Persistence Context기능
    Springboot에서는 JpaRepository 인터페이스를 확장하여 리포지토리를 정의하면, 기본적인 CRUD 기능이 자동으로 제공됩니다.

1. 엔티티의 저장
2. 엔티티의 조회
3. 엔티티의 업데이트
4. 엔티티의 삭제