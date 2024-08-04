# 1.spring-boot-starter-security
    Spring Boot 애플리케이션에서 보안 기능을 손쉽게 추가할 수 있게 해주는 
    스타터입니다. 
    Spring Security와 관련된 종속성이 자동으로 설정되고, 애플리케이션에
    기본적인 보안 설정이 적용됩니다. 이를 통해 인증 및 권한 부여를 포함한 
    다양한 보안 기능을 쉽게 구현할 수 있습니다.


# 2.기능
## 2-1.인증 및 권한 부여
    사용자 인증과 권한 부여를 관리할 수 있습니다.

## 2-2.CSRF 보호
    Cross-Site Request Forgery 공격을 방지할 수 있습니다.

## 2-3.세션 관리
    세션 고정 보호와 같은 다양한 세션 관리 기능을 제공합니다.

## 2-4.암호 저장
    안전한 암호 저장을 위한 암호화 및 해싱 기능을 제공합니다.

## 2-5.보안 필터
    보안 필터 체인을 통해 HTTP 요청을 보호합니다.



# 3.포함 애노테이션
- @EnableWebSecurity: Spring Security 웹 보안을 활성화.
- @EnableGlobalMethodSecurity: 메서드 수준 보안을 활성화.
- @PreAuthorize: 메서드가 호출되기 전에 접근 권한을 확인.
- @PostAuthorize: 메서드가 호출된 후에 접근 권한을 확인.
- @Secured: 특정 역할을 가진 사용자만 접근 가능하도록 설정.
- @RolesAllowed: 특정 역할을 가진 사용자만 접근 가능하도록 설정.
- @AuthenticationPrincipal: 현재 인증된 사용자의 Principal 객체를 메서드 - 파라미터에 바인딩.
- @WithMockUser: 테스트에서 가짜 인증된 사용자로 설정.
- @WithUserDetails: 테스트에서 사용자 상세 정보를 제공.
- @PermitAll: 특정 메서드나 클래스에 대해 모든 사용자가 접근 가능하도록 설정.
- @DenyAll: 특정 메서드나 클래스에 대해 모든 사용자의 접근을 차단.
- @Order: 보안 필터 체인의 순서를 설정.
