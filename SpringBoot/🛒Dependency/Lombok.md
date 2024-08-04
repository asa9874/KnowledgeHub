# 1.Lombok
    자바 개발에서 보일러플레이트(boilerplate) 코드를 줄여주는 라이브러리입니다.
    Lombok을 사용하면 반복적인 코드 작성 없이도 게터, 세터, 생성자, 빌더 패턴 
    등의 메서드를 자동으로 생성할 수 있습니다.

# 2. 기능
## 2-1.게터와 세터 자동 생성
    @Getter와 @Setter 애노테이션을 사용하여 클래스의 필드에 대한 게터와 세터 
    메서드를 자동으로 생성합니다.

## 2-2.생성자 자동 생성
    @NoArgsConstructor, @AllArgsConstructor, @RequiredArgsConstructor 
    애노테이션을 사용하여 다양한 유형의 생성자를 자동으로 생성합니다.

## 2-3.빌더 패턴
    @Builder 애노테이션을 사용하여 객체를 생성할 때 빌더 패턴을 쉽게 구현할 수 
    있습니다.

## 2-4.toString(), equals(), hashCode() 메서드 자동 생성
    @ToString, @EqualsAndHashCode 애노테이션을 사용하여 객체의 toString(),
    equals(), hashCode() 메서드를 자동으로 생성합니다.

## 2-5.로그 처리
    @Slf4j 등 여러 로깅 프레임워크용 애노테이션을 사용하여 로그 객체를 자동으로 
    생성합니다.


## 2-6.사용예시
```java
@Getter         // 게터 자동 생성
@Setter         // 세터 자동 생성
@ToString       // toString() 자동 생성
@NoArgsConstructor  // 기본 생성자 자동 생성
@AllArgsConstructor // 모든 필드를 매개변수로 받는 생성자 자동 생성
@RequiredArgsConstructor // final 필드만을 매개변수로 받는 생성자 자동 생성
@Builder        // 빌더 패턴 클래스 자동 생성
@Slf4j          // 로그 객체 자동 생성
public class Person {

    private Long id;
    private String name;
    private int age;

    // @RequiredArgsConstructor로 인해 name 필드를 필수 매개변수로 받는 생성자 자동 생성
    private final String requiredField;

    public static void main(String[] args) {
        // 빌더 패턴을 사용한 객체 생성
        Person person = Person.builder()
            .id(1L)
            .name("John Doe")
            .age(30)
            .requiredField("Required Value")
            .build();

        // 생성된 객체의 정보 출력
        System.out.println(person);

        // 로그 메시지 출력
        log.info("Person created: {}", person);
    }
}
```