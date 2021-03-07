# 01. 변수와 자료형
## 주석(Comment)
**//** : 한 줄 주석
**/* */** : 여러 라인 주석
'''
// 주석 사용법
/*  주석을 달아봅니다.
    주석을 달아봅니다.
    주석을 달아봅니다.
*/
'''

## 표기법
- **클래스(Class)** : 모든 단어를 대문자로 시작 ex) ClassName
- **함수/변수(Function/Variable)** : 첫 단어만 소문자로 시작 ex) functionName, number

## 변수 선언법(Variable Declaration)
- **var** : 일반적으로 통용되는 변수, 언제든지 읽기, 쓰기가 가능함
- **val** : 선언시에만 초기화 가능, 중간에 값을 변경할 수 없음. runtime시 변경되지 말아야 할 값은 val로 선언
'''
fun main() {
    var a: Int = 123
    var b: Int? = null
}
'''
- **nullable 변수** : 변수에 값이 할당되지 않았다는 것을 하나의 정보로 사용. 값이 null인 상태로 연산할 시 null pointer exception이 발생할 수 있으므로 주의해서 사용해야 한다.
- **lateinit/lazy** : 변수의 초기화를 늦출 때 사용하는 속성

## 기본 자료형(Primitive Type)
### 정수형
- **Byte** : 8 bits
- **Short** : 16 bits
- **Int** : 32 bits
- **Long** : 64 bits
**정수형의 리터럴**
코드 내에 값을 표기하는 것. 10진수, 16진수, 2진수가 가능하며 10진수가 기본
**Long**을 사용할 경우 값 뒤에 **'L'**을 붙여야 하며, 16진수를 사용할 경우 **'0x'**를 앞에 붙이고, 2진수를 사용할 경우 **'0b'**를 앞에 붙인다. Kotlin은 8진수를 지원하지 않는다. 
'''
fun main() {
    var intValue: Int = 1234
    var longValue: Long = 1234L
	var intValueByHex: Int = 0x1af
	var intValueByBin: Int = 0b10110110
}
'''

### 실수형
- **Float** : 32 bits
- **Double** : 64 bits
기본형은 **Double**이며 필요에 따라 **지수(e)**를 붙여 사용한다. **Float**를 사용할 경우 값 뒤에 **'f'**를 붙인다.
'''
fun main() {
    var doubleValue: Double = 123.5
	var doubleValueWithExp: Double = 123.5e10
	var floatValue: Float = 123.5f
}
'''

### 문자형
- **Char** : 1개의 문자만을 가질 수 있다. Kotlin은 내부적으로 유니코드 인코딩 중 한 방식인 UTF-16 BE로 관리한다. 따라서, 글자 하나가 2bytes의 메모리를 사용한다.
**Char의 리터럴** : **''**(작은 따옴표)로 문자를 감싸서 표현
'''
fun main() {
	var charValue: Char = 'a'
	var koreanCharValue: Char = '가'
}
'''

### 논리형
- **Boolean** : true와 false 둘 중 하나의 값을 저장
**Boolean의 리터럴**
'''
fun main() {
	var booleanValue: Boolean = true
}
'''

### 문자형
- **String** : 하나의 문자 이상인 문자열을 저장
'''
fun main() {
	val stringValue: String = "one line string test"
	val multilineStringValue: String = """여러 줄의 문자열,
	줄바꿈, 특수문자를 쓸 때
	사용합니다"""
}
'''