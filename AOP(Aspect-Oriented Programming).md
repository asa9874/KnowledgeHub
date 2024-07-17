# 1.AOP(Aspect-Oriented Programming)
    관점 지향 프로그래밍
    어떤 로직을 기준으로 핵심적인 관점, 
    부가적인 관점으로 나누어서 보고 그 관점을 기준으로 각각 모듈화하는것 
    (어떤 공통된 로직이나 기능을 하나의 단위로 묶는것)


# 2.AOP 개념
## 2-1.Aspect
    애플리케이션에서 여러 모듈에서 공통적으로 발생하는 부가 기능들

## 2-2.Join point
    Aspect가 적용될 수 있는 위치를 나타내며, 메서드 호출이나 객체 생성과 같은 프로그램 실행의 특정 지점을 의미
    
## 2-3.Advice
    특정 Join point에서 Aspect에 의해 취해지는 조치   
    'Before', 'After', 'Around'
## 2-4.Pointcut
    하나 이상의 Join point를 정의하는 표현식
    Advice가 적용될 위치를 결정
## 2-5.Weaving
    Pointcut에 명시된 Join point에 Advice를 적용하는 과정을 의미

# 3.Spring AOP
    트랜잭션 관리, 로깅, 보안 검사
    
    트랜잭션 관리: 스프링 AOP를 사용하여 메서드 실행을 감싸 트랜잭션이 자동으로 시작 및 종료됩니다.
    로깅 Aspect: 메서드 실행 전후에 자동으로 로그를 기록하는 Aspect가 적용됩니다.
    보안 검사: 메서드 실행 전에 사용자의 인증 상태를 확인하는 Aspect가 적용됩니다.
