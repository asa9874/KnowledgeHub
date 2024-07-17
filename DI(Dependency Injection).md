# 1.DI(Dependency Injection)
    객체 간의 의존 관계를 설정하고 관리하는 디자인 패턴     
    DI는 객체가 직접 자신의 의존성을 생성하지 않고, 외부에서 주입받는 방식으로
    인터페이스를 사이에 둬서 클래스 레벨에서는 의존관계가 고정되지 않도록 하고
    런타임 시에 관계를 동적으로 주입한다.
    
    객체 간의 결합도를 낮추고 코드의 유연성과 테스트 용이성을 높이는 데 기여한다.    


# 2.DI 사용이유
- 결합도 감소: 객체 간의 의존 관계를 외부에서 주입받기 때문에 클래스 간의 결합도가 낮아진다.
- 테스트 용이성: DI는 객체를 쉽게 모킹(mocking)하거나 대체할 수 있게 하여 단위 테스트를 용이하게한다.
- 명확한 의존 관계: 생성자나 세터 메서드를 통해 의존성을 주입받기 때문에, 클래스가 어떤 의존성을 가지고 있는지 쉽게 파악할수있다.


# 3.DI 컨테이너
    객체의 생성, 구성, 의존성 주입, 생명 주기 관리 등을 담당하는 프레임워크 또는 라이브러리
    플리케이션의 객체들이 필요로 하는 의존성을 자동으로 주입하여 결합도를 낮추고 코드의 유연성과 재사용성을높인다.
    Spring 프레임워크는 가장 널리 사용되는 DI 컨테이너 중 하나이다.


# 4.DI 예시
### 4-1.DI를 사용안한예시
    강한 결합도를 초래하며, MyRepository를 다른 구현체로 대체하기 어렵다.
```java
public class MyService {
    private MyRepository myRepository;

    public MyService() {
        this.myRepository = new MyRepository();  // MyRepository를 직접 생성
    }
}

```


### 4-2.DI 사용
    MyRepository의 다른 구현체로 쉽게 대체할 수 있다.
```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;
import org.springframework.stereotype.Repository;

@Repository
public class MyRepository {
}

@Service
public class MyService {
    private final MyRepository myRepository;

    @Autowired
    public MyService(MyRepository myRepository) {
        this.myRepository = myRepository;  // 의존성을 주입받음
    }
}


```
