# 1.Spring Boot
    Spring Framework 기반의 애플리케이션을 간편하게 
    개발하고 배포할 수 있도록 도와주는 프레임워크
    Spring Boot는 설정과 배포의 복잡성을 줄여주는 다양한 기능을 제공하며,
    개발자가 신속하게 애플리케이션을 구축할 수 있도록 설계되었습니다.


# 2. Spring Boot의 구성 요소
## 2-1.Spring Boot 스타터
- 여러 개의 스타터 의존성을 통해 특정 기능을 쉽게 추가할 수 있다.
- spring-boot-starter-web: 웹 애플리케이션 개발을 위한 스타터.
- spring-boot-starter-data-jpa: JPA 기반의 데이터 액세스를 위한 스타터.
- spring-boot-starter-security: 보안을 위한 스타터.

## 2-2.자동 설정(Autoconfiguration)
- Spring Boot는 클래스패스의 설정과 빈들을 분석하여 자동으로 필요한 설정을 구성합니다.
- @SpringBootApplication 애노테이션이 포함된 클래스를 통해 자동 설정이 활성화됩니다.

## 2-3.Spring Boot Actuator
- 애플리케이션의 메트릭스, 헬스 체크, 환경 정보 등을 제공합니다.
- 엔드포인트를 통해 애플리케이션의 상태를 모니터링할 수 있습니다.




# 3.Spring Boot 특징
## 3-1.자동 설정(Auto Configuration)
- Spring Boot는 애플리케이션의 설정을 자동으로 구성해 줍니다.
- 개발자는 복잡한 설정 없이 애플리케이션을 신속하게 시작할 수 있습니다.

## 3-2.스타터(Starter) 의존성
- Spring Boot는 여러 스타터 의존성을 제공합니다.
- 필요한 라이브러리와 설정을 한 번에 추가할 수 있습니다.

## 3-3.내장 웹 서버(Embedded Server)
- Tomcat, Jetty, Undertow와 같은 내장 웹 서버를 지원합니다.
- WAR 파일로 배포하지 않고도 JAR 파일로 독립 실행형 애플리케이션을 배포할 수 있습니다.

## 3-4.프로덕션 준비
- Spring Boot는 애플리케이션의 상태 모니터링, 메트릭스, 헬스 체크 등을 위한 프로덕션 준비 기능을 제공합니다.

## 3-5.외부 설정
- application.properties 또는 application.yml을 통해 애플리케이션 설정을 외부화

