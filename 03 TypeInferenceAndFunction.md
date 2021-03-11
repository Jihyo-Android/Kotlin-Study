# 03. 타입추론과 함수
## 타입 추론(Type Inference)
- 변수나 함수를 선언할 때나 연산이 이루어질 때 자료형을 코드에 명시하지 않아도 Kotlin이 자동으로 자료형을 추론하는 기능
```{.kotlin}
fun main() {
    var a = 1234 // Int
    var b = 1234L // Long
    
    var c = 12.45 // Double
    var d = 12.45f // Float

    var e = 0xABCD // Int
    var f = 0b01010101 // Int

    var g = true // Boolean
    var h = 'c' // Char
}
```

## 함수(Function)
- 함수는 특정한 동작을 하거나 원하는 결과값을 연산하는데 사용하는 기능
```{.kotlin}
fun 함수명(인자1: 자료형, 인자2: 자료형): 반환형 {
    실행문
    return ...
}
```
- ex) println() 등
```{.kotlin}
fun main() {
    println(add(5, 6, 7))
}

fun add(a: Int, b: Int, c: Int): Int {
    return a + b + c
}
```

### 단일표현식 함수(Single-Expression Function)
- 함수의 기능을 간단하게 기술할 수 있도록 지원하는 기능
- 반환형의 타입 추론이 가능하기 때문에 반환형을 생략할 수 있다
```{.kotlin}
fun main() {
    println(add(5, 6, 7))
}

fun add(a: Int, b: Int, c: Int) = a + b + c