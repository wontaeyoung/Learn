# Any, AnyObject

---

- 데이터 타입은 아니지만, 데이터 타입의 위치에서 작동하는 키워드

### Any

- Swift의 모든 타입을 지칭하는 키워드
- Mark : - Any

```swift
var someAny : Any = 100
someAny = "어떤 타입도 수용 가능"
someAny = 123.12
// Int -> String -> Float처럼 서로 다른 타입간의 할당에 엄격한 Swift임에도 모든 타입 할당 가능

let someDouble : Double = someAny (x) 
// 현재 타입이 Double이더라도 Double 타입 변수에 할당 불가
// Any에 할당된 현재 값의 타입이 할당할 변수의 타입과 일치한다하더라도 두 변수의 타입은 기본적으로 다르므로 불가
```

### AnyObject

- 모든 클래스 타입을 지칭하는 프로토콜
- MARK : - AntObject

```swift
class SomeClass{}
var someAnyObject : AnyObject = SomeClass() // 변수에 클래스로 할당할 수 있는듯?
/// 클래스 선언할 때는 {}인데 변수에 할당할때는 왜 ()이지 함수도 아닌데

someAnyObject = 123.12 (x) // AnyObject 타입에 일반 데이터 타입 값을 할당하려고 하면 오류 발생

참고# : Swift의 모든 데이터 타입은 구조체로 되어있다
```

# nil

- 없음을 의미하는 키워드

```swift
var someAny : Any = 100
someAny = nil (x) // Any 타입은 어떤 값도 들어올 수 있지만 nil(값이 없음)값은 할당할 수 없음

참고# : nil은 어딘가에 할당할 수 있는 값은 아님, 추후 옵셔널 강의에서 배울 예정
```
