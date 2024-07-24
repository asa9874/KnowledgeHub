# 1.DTO(Data Transfer Object)
    계층 간 데이터 전송을 위해 사용되는 객체입니다.
    일반적으로, DTO는 데이터베이스 엔티티나 비즈니스 로직을 직접 노출하지 않고, 
    특정 뷰나 API 응답을 위한 데이터 구조를 정의합니다.
    주로 Client 와 Controller 사이에서 DTO 가 사용됩니다.

```java
public class UserDTO {
    private Long id;
    private String name;
    private String email;

    // Getters and Setters
}
```

# 2.DTO 역할
## 2-1.데이터 캡슐화
    DTO는 필요한 데이터만 캡슐화하여 다른 계층이나 시스템 간에 전송합니다.

## 2-2.데이터 변환
    엔티티와 DTO 간의 변환을 통해, 
    비즈니스 로직과 표현 로직을 분리할 수 있습니다.

## 2-3.보안
    민감한 데이터를 제외하거나 필요한 데이터만 포함하여 전송할 수 있습니다.

## 2-4.직렬화
    DTO는 직렬화 및 역직렬화가 용이하여, 네트워크 전송이나 JSON/XML 등으로
    변환할 때 유리합니다.





# 3. 사용할때 vs 안 사용할때
## 사용할때

```java
@Service
public class UserService {

    @Autowired
    private UserRepository userRepository;

    public UserDTO createUser(UserDTO userDTO) {
        User user = new User();
        user.setName(userDTO.getName());
        user.setEmail(userDTO.getEmail());
        user = userRepository.save(user);
        return convertToDTO(user);
    }

    public Optional<UserDTO> getUserById(Long id) {
        return userRepository.findById(id).map(this::convertToDTO);
    }

    public List<UserDTO> getUsersByName(String name) {
        return userRepository.findByName(name).stream()
                             .map(this::convertToDTO)
                             .collect(Collectors.toList());
    }

    public UserDTO updateUser(Long id, UserDTO userDTO) {
        User user = userRepository.findById(id).orElseThrow(() -> new RuntimeException("User not found"));
        user.setName(userDTO.getName());
        user.setEmail(userDTO.getEmail());
        user = userRepository.save(user);
        return convertToDTO(user);
    }

    public void deleteUser(Long id) {
        userRepository.deleteById(id);
    }

    private UserDTO convertToDTO(User user) {
        UserDTO userDTO = new UserDTO();
        userDTO.setId(user.getId());
        userDTO.setName(user.getName());
        userDTO.setEmail(user.getEmail());
        return userDTO;
    }
}
```


## 사용안할때
```java
@Service
public class UserService {

    @Autowired
    private UserRepository userRepository;

    public User createUser(User user) {
        return userRepository.save(user);
    }

    public Optional<User> getUserById(Long id) {
        return userRepository.findById(id);
    }

    public List<User> getUsersByName(String name) {
        return userRepository.findByName(name);
    }

    public User updateUser(Long id, User userDetails) {
        User user = userRepository.findById(id).orElseThrow(() -> new RuntimeException("User not found"));
        user.setName(userDetails.getName());
        user.setEmail(userDetails.getEmail());
        return userRepository.save(user);
    }

    public void deleteUser(Long id) {
        userRepository.deleteById(id);
    }
}
```