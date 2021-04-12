# 28. lateinit, lazy 변수

## var
var 변수는 이미 할당된 경우에도 다른 객체로 다시 할당할 수 있다
```kotlin
var a = Person("유나", 2003)
a = Person("루다", 1997)
```

## val
val 변수는 한 번 할당된 경우 할당된 객체를 바꿀 수 없고 객체 내부의 속성을 변경할 수 없는 것은 아니다

## 상수 (Constant)
- 객체의 내부 속성 또한 **절대 변경이 불가능**한 것
- 컴파일 시점에 결정되어 절대 바꿀 수 없는 값
- 선언 규칙 : **대문자**와 **언더스코어(_)**만 사용
- 상수로 선언될 수 있는 값은 **기본 자료형(String 포함)**만 가능하며 런타임에 생성될 수 있는 일반적인 다른 클래스의 객체들은 담을 수 없다
- **클래스의 속성이나 지역 변수 등으로는 사용할 수 없다**
- 반드시 **companion object** 안에 선언하여 객체의 생성과 관계없이 클래스와 관계된 **고정값**으로만 사용하게 된다

```kotlin
class Sample {
    companion object {
        const val CONST_A = 1234
    }
}
```

### 상수를 사용하는 이유
변수의 경우 런타임시 객체를 생성하는 데 시간이 더 소요되어 성능이 하락이 있다. 따라서, 늘 고정적으로 사용할 값은 상수를 통해 객체의 생성없이 메모리에 값을 고정하여 사용함으로써 성능을 향상시킨다

### 사용 예시
```kotlin
fun main() {
    val foodCourt = FoodCourt()

    foodCourt.searchPrice(FoodCourt.FOOD_CREAM_PASTA)
    foodCourt.searchPrice(FoodCourt.FOOD_STEAK)
    foodCourt.searchPrice(FoodCourt.FOOD_PIZZA)
}

class FoodCourt {
    fun searchPrice(foodName: String) {
        val price = when (foodName) {
            FOOD_CREAM_PASTA -> 13000
            FOOD_STEAK -> 25000
            FOOD_PIZZA -> 15000
            else -> 0
        }
    }

    // searchPrice()에서 사용할 음식 이름을 상수로 선언
    companion object{
        const val FOOD_CREAM_PAST = "크림 파스타"
        const val FOOD_STEAK = "스테이크"
        const val FOOD_PIZZA = "피자"
    }
}
```

## lateinit
- 변수에 객체를 할당하는 것을 선언과 동시에 하지 못할 경우에 사용
- 위의 경우 변수만 선언하고 초기값의 할당은 나중에 할 수 있도록 하는 키워드

### lateinit var 변수의 제한사항
1. 초기값 할당 전까지 변수를 사용할 수 없음 (에러 발생)
2. 기본 자료형에는 사용할 수 없음 (String 클래스에는 사용 가능)
3. **초기화**여부는 **::변수.isInitialized**를 통해 확인 가능

```kotlin
fun main() {
    val a = LateInitSample()

    println(a.getLateInitText())
    a.text = "새로 할당한 값"
    println(a.getLateInitText())
}

class LateInitSample {
    lateinit var text: String

    fun getLateInitText(): String {
        if(::text.isInitialized) {
            return text
        } else {
            return "기본값"
        }
    }
}
```

## lazy delegate property (지연 대리자 속성)
- 변수를 사용하는 시점까지 초기화를 자동으로 늦춤
- 람다 함수 형태로 선언시 즉시 객체를 생성 및 할당하여 변수를 초기화하는 형태를 갖고 있지만 실제 실행시에는 **해당 변수를 사용하는 시점**에 초기화된다
- 람다함수로 구현되기 때문에 여러 문장이 들어갈 수 있지만 **마지막 구문**으로 초기화된다
```kotlin
fun main() {
    val number: Int by lazy {
        println("초기화를 합니다")
        7
    }

    println("코드를 시작합니다")
    println(number)
    println(number)
}
```
