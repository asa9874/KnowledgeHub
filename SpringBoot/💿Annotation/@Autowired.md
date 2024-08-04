# 1.@Autowired
    의존성 주입(Dependency Injection)을 수행하기 위해 사용되는 
    어노테이션입니다. 이 어노테이션을 통해 Spring 컨테이너가 관리하는 빈을 
    자동으로 주입할 수 있습니다.


# 2.기능
## 2-1.자동 의존성 주입
    Spring 컨테이너에서 관리하는 빈을 자동으로 주입할 수 있습니다.

## 2-2.필드 주입
    클래스의 필드에 직접 주입할 수 있습니다.
```java
@Service
public class MyService {

    @Autowired // MyRepository 빈을 주입합니다.
    private MyRepository myRepository;

    public void performAction() {
        myRepository.doSomething();
    }
}
```

## 2-3.생성자 주입
    클래스의 생성자에 주입할 수 있습니다.

```java
@Service
public class MyService {

    private final MyRepository myRepository;

    @Autowired // 생성자에 MyRepository 빈을 주입합니다.
    public MyService(MyRepository myRepository) {
        this.myRepository = myRepository;
    }

    public void performAction() {
        myRepository.doSomething();
    }
}
```
## 2-4.세터 메서드 주입
    클래스의 세터 메서드에 주입할 수 있습니다.

```java
@Service
public class MyService {

    private MyRepository myRepository;

    @Autowired // 세터 메서드에 MyRepository 빈을 주입합니다.
    public void setMyRepository(MyRepository myRepository) {
        this.myRepository = myRepository;
    }

    public void performAction() {
        myRepository.doSomething();
    }
}
```
## 2-5.기본 생성자
    기본 생성자를 사용하여 빈을 주입할 수 있습니다.
