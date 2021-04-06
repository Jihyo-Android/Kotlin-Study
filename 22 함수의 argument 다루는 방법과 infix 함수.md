# 22. 함수의 argument 다루는 방법과 infix 함수

## 오버로딩 (Overloading)
- **같은 Scope 안**에서 같은 이름의 함수를 여러 개 생성할 수 있다
- 이름이 같더라도 패러미터의 자료형 및 개수가 다른 경우 다른 함수로 동작할 수 있다

```kotlin
fun main() {
    read(7)
    read("갑사합니다")
}

fun read(x: Int) {
    println("숫자 $x 입니다")
}

fun read(x: String) {
    println(x)
}
```

## default arguments
패러미터를 받아야 하는 함수이지만 별다른 패러미터가 없더라도 기본값으로 동작하기 위해 사용

## named arguments
패러미터의 순서와 관계없이 패러미터의 이름을 사용하여 직접 패러미터의 값을 할당

```kotlin
fun main() {
    // default arguments
    deliveryItem("짬뽕")
    deliveryItem("책", 3)
    deliveryItem("노트북", 30, "학교")

    // named arguments
    deliveryItem("선물", destination = "친구집")
}

fun deliveryItem(name: String, count: Int = 1, destination: String = "집") {
    println("${name}, ${count}개를 ${destination}에 배달하였습니다")
}
```

## vararg (variable number of arguments)
- 같은 자료형을 개수에 상관없이 패러미터로 받고 싶을 때 사용
- **vararg**는 for문으로 참조가 가능
- 개수가 지정되지 않은 패러미터라는 특징이 있으므로, 다른 패러미터와 같이 사용할 때는 **맨 마지막**에 위치해야 한다

```kotlin
fun main() {
    sum(1, 2, 3, 4)
}

fun sum(vararg numbers: Int) {
    var sum = 0
    
    for (n in numbers) {
        sum += n
    }

    print(sum)
}
```

## infix 함수
**class 안에서 infix 함수를 선언**할 때에는 적용할 클래스가 자기 자신이므로 **클래스 이름은 쓰지 않는다**

### 형태
infix fun 자료형.함수명(패러미터: 자료형): 반환형 = 반환문

```kotlin
fun main() {
    println(6 multiply 4)
    println(6.multipl(4))
}

infix fun Int.multiply(x: Int): Int = this * x
```