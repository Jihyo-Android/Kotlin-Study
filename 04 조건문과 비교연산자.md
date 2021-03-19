# 04 조건문과 비교연산자
## if 조건문
- if문에 주어진 값이 **'참'**이라면 따라오는 구문을 실행하는 기능
```{.kotlin}
fun main() {
    var a: Int = 7
    if (a > 10) {
        println("a는 10보다 크다")
    } else {
        println("a는 10보다 작거나 같다")
    }
}
```

## 비교연산자(Comparison Operator)
|연산자|의미|
|:-------------------------------------------------:|
| < | 왼쪽이 작으면 true, 크면 false 반환	          | 
|<= | 왼쪽이 작거나 같으면 true, 아니면 false 반환	   |
| > | 왼쪽이 크면 true, 작으면 false 반환	          |
|>= | 왼쪽이 크거나 같으면 true, 아니면 false 반환     |
|!= | 두 개 항의 값이 다르면 true, 아니면 false 반환   |
|== | 두 개 항의 값이 같으면 true, 아니면 false 반환   |
|===| 두 개 항의 참조가 같으면 true, 아니면 false 반환 |
|!==| 두 개 항의 참조가 다르면 true, 아니면 false 반환 |	

### is 연산자
- 자료형이 맞는지 체크, 맞다면 true, 아니면 false 반환
```{.kotlin}
fun main() {
    var a: Int = 10

    if (a is Int) println("a는 정수형입니다.")
}
```

## 다중 조건문 When
- 다른 언어에서 사용되는 **swith**문과 유사
- 하나의 변수를 여러 개의 값과 비교할 수 있다
- 여러 개의 조건에 부합될 경우 먼저 부합하는 조건이 실행된다
```{.kotlin}
fun main() {
    doWhen(1)
    doWhen(12L)
    doWhen(3.14159)
    doWhen("Kotlin")
}

// 파라미터는 Any를 사용한다. 어떤 자료형과도 호환되는 최상위 자료형이다.
fun doWhen(a: Any) {
    when(a) {
        1 -> println("정수 1입니다")
        is Long -> println("Long 타입입니다")
        !is String -> println("String 타입이 아닙니다")
        else -> println("어떤 조건도 만족하지 않습니다")
    }
}
```

- when의 조건이 맞을 때 **동작대신 값을 반환**하는 **표현식**으로서의 역할
- when의 결과를 **변수에 할당**하거나 직접 **값으로서 사용**할 수 있다
```{.kotlin}
fun doWhen(a: Any) {
    when(a) {
        1 -> "정수 1입니다"
        is Long -> "Long 타입입니다"
        !is String -> "String 타입이 아닙니다"
        else -> "어떤 조건도 만족하지 않습니다"
    }
}
```

- when에서 결과를 **변수에 받아 출력**해보려면
```{.kotlin}
fun doWhen(a: Any) {
    var result = when(a) {
        1 -> "정수 1입니다"
        is Long -> "Long 타입입니다"
        !is String -> "String 타입이 아닙니다"
        else -> "어떤 조건도 만족하지 않습니다"
    }
    println(result)
}
```

