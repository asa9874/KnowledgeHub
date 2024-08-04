# 1.@Transactional
    Spring Framework에서 트랜잭션 관리를 선언적으로 처리할 수 있도록 돕는 
    애노테이션입니다. 트랜잭션의 시작, 커밋, 롤백을 개발자가 직접 코딩하지 
    않고도 자동으로 처리할 수 있습니다.


# 2.@Transactional 기능
## 2-1.트랜잭션의 시작과 종료 자동 관리
    @Transactional이 붙은 메서드가 호출될 때 Spring은 트랜잭션을 시작하고, 
    메서드 실행이 완료되면 커밋합니다.
    메서드 내에서 예외가 발생하면 트랜잭션을 롤백합니다.
```java
@Service
public class UserService {

    @Autowired
    private UserRepository userRepository;

    @Transactional
    public User createUser(User user) {
        return userRepository.save(user);
    }

    @Transactional
    public void updateUser(Long id, User userDetails) {
        User user = userRepository.findById(id).orElseThrow(() -> new RuntimeException("User not found"));
        user.setName(userDetails.getName());
        user.setEmail(userDetails.getEmail());
        userRepository.save(user);
    }
}
```
## 2-2.트랜잭션 전파
    트랜잭션 전파는 메서드가 호출될 때 트랜잭션을 어떻게 처리할지를 정의합니다.
    예를 들어, 새로운 트랜잭션을 시작하거나 기존 트랜잭션을 사용할 수 있습니다.
```java
@Transactional(propagation = Propagation.REQUIRES_NEW)
public void performNewTransaction() {
    // 이 메서드는 항상 새로운 트랜잭션에서 실행됩니다.
}
```
## 2-3.트랜잭션 격리 수준
    트랜잭션 격리 수준은 동시에 실행되는 트랜잭션 간의 상호작용을 정의합니다. 
    격리 수준에 따라 다른 트랜잭션의 작업이 현재 트랜잭션에 영향을 미칠 수 
    있습니다.
```java
@Transactional(isolation = Isolation.SERIALIZABLE)
public void performIsolatedTransaction() {
    // 이 메서드는 SERIALIZABLE 격리 수준에서 실행됩니다.
}
```
## 2-4.읽기 전용 트랜잭션
    @Transactional(readOnly = true)를 설정하면, 트랜잭션이 읽기 전용으로 
    설정되어 쓰기 작업이 없음을 보장합니다.
```java
@Transactional(readOnly = true)
public List<User> getAllUsers() {
    // 이 메서드는 읽기 전용 트랜잭션에서 실행됩니다.
    return userRepository.findAll();
}
```
## 2-5.타임아웃 설정
    timeout 속성을 사용하여 트랜잭션이 완료되기까지 기다리는 최대 시간을 설정할
    수 있습니다.
```java
@Transactional(timeout = 30)
public void performTransactionWithTimeout() {
    // 이 메서드는 30초 동안만 트랜잭션이 유지됩니다.
}
```
## 2-6.롤백 규칙
    rollbackFor와 noRollbackFor 속성을 통해 특정 예외 발생 시 트랜잭션을 
    롤백하거나 롤백하지 않도록 설정할 수 있습니다.

```java
@Transactional(rollbackFor = CustomException.class)
public void performTransaction() throws CustomException {
    // CustomException이 발생하면 트랜잭션이 롤백됩니다.
}
```
