# 1.spring-boot-starter-web
    Spring Boot 애플리케이션에 웹 기능을 쉽게 추가할 수 있도록 지원하는 
    스타터입니다. 이 스타터를 사용하면 Spring MVC, REST, 및 Tomcat과 같은 
    내장된 웹 서버를 손쉽게 설정할 수 있습니다.

# 2.기능
## 2-1.Spring MVC
    웹 애플리케이션을 위한 Model-View-Controller 아키텍처 지원.
    
## 2-2.RESTful 웹 서비스
    REST API를 쉽게 구축할 수 있는 기능.

## 2-3.내장 웹 서버
    기본적으로 Tomcat 사용 가능.

## 2-4.Jackson
    JSON 직렬화 및 역직렬화를 위한 기본 지원.

## 2-5.Validation
    데이터 검증을 위한 지원.




# 3.포함 애노테이션
- @Controller: Spring MVC에서 컨트롤러 역할을 하는 클래스를 정의.
- @RestController: @Controller와 @ResponseBody를 결합하여 RESTful 웹 서비스를 정의.
- @RequestMapping: HTTP 요청을 특정 핸들러 메서드와 매핑.
- @GetMapping: HTTP GET 요청을 특정 핸들러 메서드와 매핑.
- @PostMapping: HTTP POST 요청을 특정 핸들러 메서드와 매핑.
- @PutMapping: HTTP PUT 요청을 특정 핸들러 메서드와 매핑.
- @DeleteMapping: HTTP DELETE 요청을 특정 핸들러 메서드와 매핑.
- @PatchMapping: HTTP PATCH 요청을 특정 핸들러 메서드와 매핑.
- @RequestParam: 요청 매개변수를 메서드 파라미터에 바인딩.
- @PathVariable: URI 경로 변수를 메서드 파라미터에 바인딩.
- @ModelAttribute: 모델 데이터를 메서드 파라미터에 바인딩.
- @RequestBody: HTTP 요청 본문을 메서드 파라미터에 바인딩.
- @ResponseBody: 메서드의 반환 값을 HTTP 응답 본문으로 변환.
- @ResponseStatus: 메서드가 반환하는 HTTP 응답 상태 코드를 설정.
- @ExceptionHandler: 예외를 처리하는 메서드를 정의.
- @InitBinder: 커스텀 데이터 바인딩 로직을 정의.
- @SessionAttributes: 세션에 저장할 모델 속성을 정의.
- @CrossOrigin: CORS 설정을 정의.