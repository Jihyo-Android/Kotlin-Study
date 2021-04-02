# 18. 캐스팅을 줄여주는 Generic

## 제너릭 (Generic)
- 클래스나 함수에서 사용하는 자료형을 외부에서 지정할 수 있는 기능
- 캐스팅은 프로그램의 속도를 저하시킬 수 있다는 단점이 존재
- 제너릭은 고정적인 자료형 대신 실제 자료형으로 대체되는 **타입 패러미터**를 받아 사용

### 타입 패러미터(Type Parameter)
- 클래스 이름과 규칙이 같지만 일반적으로 **<T>**를 사용하는 것이 관례
- 여러 개의 제너릭을 사용할 경우 <T, U, V>를 사용

### 예시
```kotlin
fun <Int> genericFunc(param: Int): Int
class GenericClass<Int>(var pref: Int)

// 특정한 수퍼 클래스를 상속받은 클래스 타입으로만 제한
<T: SuperClass>
```

### 제너릭의 사용
```kotlin
fun main() {
    UsingGeneric(A()).doShouting()
    UsingGeneric(B()).doShouting()
    UsingGeneric(C()).doShouting()

    doShouting(B())
}

fun <T: A> doShouting(t: T) {
    t.shout()
}

open class A {
    open fun shout() {
        println("A가 소리칩니다")
    }
}

class B: A() {
    override fun shout() {
        println("B가 소리칩니다")
    }
}

class C: A() {
    override fun shout() {
        println("C가 소리칩니다")
    }
}

class UsingGeneric<T: A> (val t: T) {
    fun doShouting() {
        t.shout()
    }
}
```