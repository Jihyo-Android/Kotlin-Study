# 02. 형변환과 배열
## 형변환(Type Casting)
- 하나의 변수에 지정된 자료형을 호환되는 다른 자료형으로 변경하는 기능
- 논리형은 변환될 수 없다
- **명시적 형변환** : 변환될 자료형을 개발자가 직접 지정함
- **암시적 형변환** : 변수를 할당할 시 자료형을 지정하지 않아도 자동으로 형변환됨
- Kotlin은 형변환시 발생할 수 있는 오류를 막기위해 다른 언어들이 지원하는 '암시적 형변환'은 지원하지 않는다
```{.kotlin}
fun main() {
    var a: Int = 54321
    var b: Byte = a.toByte()
    var c: Short = a.toShort()
    // var c: Int = a.toInt()
    var d: Long = a.toLong()
    var e: Float = a.toFloat()
    var f: Double = a.toDouble()
    var g: Char = a.toChar()
    var h: String = a.toString()
}
```

## 배열(Array)
- 배열은 내부적으로 **Array 클래스**로 제공
```{.kotlin}
fun main() {
    var intArr = arrayOf(1, 2, 3, 4, 5)

    // 크기가 5인 비어있는 배열
    var nullArr = arrayOfNulls<Int>(5)

    intArr[2] = 8
    println(intArr[4])
}