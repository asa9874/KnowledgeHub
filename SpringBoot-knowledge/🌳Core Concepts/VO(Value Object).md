# 1.VO(Value Object)
    도메인에서 한 개 또는 그 이상의 속성들(primitive 타입이다.)
    을 묶어서 특정 값을 나타내는 객체
    
    데이터 모델에서 값이나 상태를 표현하는 객체입니다.
    주로 객체의 불변성을 보장하고, 해당 객체가 고유한 의미를 가지도록 하기 
    위해 사용됩니다.
    데이터를 안전하게 캡슐화하고, 코드의 명확성과 일관성을 유지할 수 있습니다.


# 2.VO 특성
## 2-1.불변성(Immutability)
    VO는 생성 후 그 상태를 변경할 수 없는 불변 객체입니다.
    (수정자(Setter) 메소드를 가지지 않습니다.)
    한번 생성된 VO의 값은 변경되지 않으며, 새로운 값을 갖는 새로운 VO 객체를 
    생성해야 합니다.

## 2-2.값 기반의 동등성(Value-Based Equality)
    VO는 객체의 동등성을 값을 기반으로 판단합니다. 
    즉, 두 VO 객체가 같은 값을 가지면 동일하다고 여깁니다. 
    예를 들어, 두 Money 객체가 같은 금액과 통화를 가지고 있다면, 이 두 객체는 
    동일한 것으로 간주됩니다.


## 2-3.간단한 표현
    VO는 주로 단순한 값을 표현합니다. 예를 들어, Money라는 VO는 금액과 통화를
    나타내며, Address라는 VO는 주소 정보를 나타낼 수 있습니다.




# 3.예시(Money 클래스) 
```java

// Money라는 VO 클래스 정의
public class Money {
    private final double amount; // 금액을 나타내는 필드
    private final String currency; // 통화를 나타내는 필드

    // 생성자: 객체 생성 시 필드 값을 초기화
    public Money(double amount, String currency) {
        this.amount = amount;
        this.currency = currency;
    }

    // 금액을 반환하는 메서드
    public double getAmount() {
        return amount;
    }

    // 통화를 반환하는 메서드
    public String getCurrency() {
        return currency;
    }

    // equals() 메서드 오버라이드: 값 기반 동등성 비교
    @Override
    public boolean equals(Object o) {
        if (this == o) return true; // 자기 자신과 비교 시 true 반환
        if (o == null || getClass() != o.getClass()) return false; // null이나 다른 클래스 타입일 경우 false 반환
        Money money = (Money) o;
        return Double.compare(money.amount, amount) == 0 && // 금액이 같으면 true
               currency.equals(money.currency); // 통화가 같으면 true
    }

    // hashCode() 메서드 오버라이드: 해시코드 계산
    @Override
    public int hashCode() {
        return Objects.hash(amount, currency); // 금액과 통화를 바탕으로 해시코드 계산
    }

    // toString() 메서드 오버라이드: 객체를 문자열로 표현
    @Override
    public String toString() {
        return amount + " " + currency; // "금액 통화" 형식으로 반환
    }
}

```


```java
// Order 클래스 정의
public class Order {
    private final Money totalAmount; // 총액을 표현하는 Money VO 필드

    // 생성자: Order 객체를 생성할 때 총액을 초기화
    public Order(Money totalAmount) {
        this.totalAmount = totalAmount;
    }

    // 총액을 반환하는 메서드
    public Money getTotalAmount() {
        return totalAmount;
    }

    // toString() 메서드 오버라이드: Order 객체를 문자열로 표현
    @Override
    public String toString() {
        return "Order total: " + totalAmount; // "Order total: 금액 통화" 형식으로 반환
    }
}
```