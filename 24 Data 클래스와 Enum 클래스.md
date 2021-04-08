# 24. Data 클래스와 Enum 클래스

## Data 클래스
데이터를 다루는 데 최적화 된 클래스

### Data 클래스의 기능
- **5가지 기능**을 내부적으로 자동으로 생성
- 사용자가 직접 호출하기 위한 함수가 아닌 **배열이나 리스트 등에 Data 클래스의 객체가 담겨있을 때** 내용을 자동으로 꺼내 쓸 수 있는 기능을 지원하기 위한 함수

1. **equals()** : 내용의 동일성을 판단
2. **hashCode()** : 객체의 내용에서 고유한 코드를 생성
3. **toString()** : 포함된 속성을 보기쉽게 나타냄
4. **copy()** : 객체를 복사하여 똑같은 내용의 새 객체를 만듦. 패러미터가 있다면 일부 속성을 변경하여 생성할 수 있음
5. **componentX()** : 속성을 순서대로 반환. 내부적으로 **component1()**, **component2()** 함수를 사용

```kotlin
fun main() {
    val a = General("보영", 212)

    println(a == General("보영", 221))
    println(a.hashCode())
    println(a)

    val b = Data("루다", 306)
    
    println(b == General("루다", 306))
    println(b.hashCode())
    println(b)

    println(b.copy())
    println(b.copy("아린"))
    println(b.copy(id = 618))

    val list = listOf(Data("보영", 212),
                    Data("루다", 306),
                    Data("아린", 618))

    for ((a, b) in list) {
        println("${a}, {b}")
    }
}

class General(val name: String, val id: Int)

data class Data(val name: String, val id: Int)
```

### 결과
**General 클래스**로 만든 **a**는 **equals()**나 **hashCode**, **toString()** 함수의 결과가 **제대로 구현되지 않은** 반면 **data class**로 만든 **b**는 세 함수 모두 **의미있는 기능**으로 자동 구현되어 있음을 알 수 있으며 **copy()** 함수를 통해 **원본을 복사한 새 객체** 역시 쉽게 만들 수 있음을 알 수 있다

## Enum 클래스
- **Enum** : Enumerated Type으로 **열거형**을 의미
- **enum 클래스** 안의 객체들은 관행적으로 상수를 나타낼 때 사용하는 **대문자로 기술**
- enum의 객체들은 고유한 속성을 가질 수 있다
- 일반 클래스처럼 **함수도 가질 수 있다**

### 예시
```kotlin
enum class Color (val number: Int) {
    RED(1),
    BLUE(2),
    GREEN(3);

    fun isRed() = this == Color.RED
}
```

```kotlin
fun main() {
    var state = State.SING
    println(state)

    state = State.SLEEP
    println(state.isSleeping())

    state = State.EAT
    println(state.message)
}

enum class State(val essage: String) {
    SING("노래를 부릅니다"),
    EAT("밥을 먹습니다"),
    SLEEP("잠을 잡니다");

    fun isSleeping() = this == State.SLEEP
}
```