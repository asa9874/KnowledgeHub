# 1.thymeleaf-extras-springsecurity6
    Thymeleaf 템플릿 엔진을 사용하는 Spring Boot 애플리케이션에서 Spring 
    Security와의 통합을 지원하는 모듈입니다. Spring Security의 기능을 
    Thymeleaf 템플릿에서 쉽게 사용할 수 있으며, 인증 및 권한 검사와 같은 
    기능을 템플릿 내에서 구현할 수 있습니다.


# 2. 기능
## 2-1.인증된 사용자 정보 접근
    로그인한 사용자 정보에 접근할 수 있습니다.

## 2-2.권한 검사
    템플릿 내에서 사용자의 권한을 검사할 수 있습니다.

## 2-3.로그인/로그아웃 처리
    로그인 및 로그아웃 처리를 쉽게 구현할 수 있습니다.

## 2-4.보안 속성 사용
    보안 관련 속성들을 사용하여 조건부 렌더링을 할 수 있습니다.


# 3.주요 속성
## 3-1.sec:authorize
    조건이 만족될 때만 해당 요소를 렌더링합니다.
```html
<p sec:authorize="hasRole('ROLE_ADMIN')">This is for admins only</p>
```

## 3-2.sec:authentication
    현재 인증된 사용자에 대한 정보를 표시합니다.
```html
<span sec:authentication="principal.username"></span>
```

## 3-3.sec:authorize-url
    URL 접근에 대한 권한 검사를 수행합니다.
```html
<a th:href="@{/admin}" sec:authorize-url="hasRole('ROLE_ADMIN')">Admin Page</a>
```

## 3-4.sec:csrf
    CSRF 토큰을 폼에 추가합니다.
```html
<input type="hidden" sec:csrf/>
```