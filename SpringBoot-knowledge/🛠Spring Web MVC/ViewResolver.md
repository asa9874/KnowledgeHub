# 1.ViewResolver
    Spring MVC에서 뷰(View)를 결정하는 역할을 담당하는 컴포넌트입니다.
    Spring Boot에서는 자동으로 적절한 ViewResolver를 설정해준다.
    
    클라이언트의 요청을 처리한 후, 컨트롤러가 반환한 뷰 이름을 실제 뷰 파일
    (예: JSP, Thymeleaf, FreeMarker 등)로 매핑하는 과정에서 사용

# 2.ViewResolver 역할
## 2-1.뷰 이름 매핑
- 컨트롤러가 반환하는 뷰 이름을 실제 뷰 파일의 경로로 변환
- 예를 들어, "home"이라는 뷰 이름을 /WEB-INF/views/home.jsp와 같은 경로로 변환

## 2-2.뷰 파일 반환
- 매핑된 뷰 파일을 클라이언트에게 렌더링하여 최종 HTML 응답을 생성


# 3.ViewResolver 구현체
## 3-1.InternalResourceViewResolver
- JSP와 같은 내부 자원 뷰를 처리합니다.
- 뷰 이름을 JSP 파일의 경로로 변환하여 반환합니다.

## 3-2.ThymeleafViewResolver
- Thymeleaf 템플릿 엔진을 사용하는 뷰 리졸버입니다.
- 뷰 이름을 Thymeleaf 템플릿 파일의 경로로 변환합니다
