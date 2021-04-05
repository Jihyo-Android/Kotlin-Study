# 20. null 처리와 동일성의 확인


## null 처리
**null**인 상태에서 속성이나 함수를 사용하려 하면 **null pointer exception**이 발생하기 때문에 null 체크가 필요하다

### null safe 연산자
- **?.**(null safe operator) : 참조 연산자를 실행하기 전 **먼저 객체가 null인지 확인**하고 객체가 **null이라면 뒤의 구문을 실행하지 않는다** ex) **sample?.toUpperCase()**

- **?:**(elivis operator) : 객체가 null이 아니라면 그대로 사용하지만 **null이라면 연산자 우측의 객체로 대체된다** ex) **sample?:"default"**

- **!!.**(non-null assertion operator) : 참조 연산자를 사용할 때 **null 여부**를 컴파일시 **확인하지 않도록** 하여 **런타임시 null pointer exception이 나도록 방치한다**

```kotlin
fun main() {
    var a: String? = null

    println(a?.toUpperCase())

    println(a?:"default".toUpperCase())

    println(a!!.toUpperCase())
}
```

### 스코프 함수와의 사용
```kotlin
fun main() {
    var a: String? = null

    // a가 null일 경우 실행되지 않지만
    // null이 아닐 경우 두 구문 모두 실행된다
    a?.run {
        println(toUpperCase())
        println(toLowerCase())
    }
}
```

## 변수의 동일성

### 내용의 동일성
- **==** : 내용의 동일성을 확인하는 연산자
- 서로 다른 변수가 메모리 상의 서로 다른 곳에 할당된 객체이더라도 그 내용이 같다면 동일하다고 판단
- 내용의 동일성은 **자동으로 판단되지 않고** Kotlin의 모든 클래스가 내부적으로 상속받는 **Any**라는 최상위 클래스의 **equals()**가 반환하는 **Boolean**값으로 판단한다. 따라서, custom 클래스를 사용할 때는 equals() **override하여** 동일성을 확인해주는 구문을 구현해야 한다

#### 객체의 동일성
- **===** : 객체의 동일성을 확인하는 연산자
- 서로 다른 변수가 메모리 상의 같은 객체를 가리킬 때만 동일하다고 판단

```kotlin
fun main() {
    var a = Product("콜라", 1000)
    var a = Product("콜라", 1000)
    var c = a
    var a = Product("사이다", 1000)

    println(a == b)
    println(a === b)

    println(a == c)
    println(a === c)

    println(a == d)
    println(a === d)
}

class Product(val name: String, val price: Int) {
    override fun equals(other: Any?): Boolean {
        if (other is Product) {
            return other.name == name && other.price == price
        } else {
            return false
        }
    }
}
```