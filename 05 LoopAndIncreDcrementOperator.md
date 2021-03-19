# 04. 반복문과 증감연산자
## 반복문의 형태
- **조건형 반복문** : 조건이 참인 경우 반복을 유지
- **범위형 반복문** : 반복 범위를 정해 반복을 수행

## 조건형 반복문
### while
- while문의 조건이 거짓이 되면 반복을 중단하고 다음 구문으로 넘어간다
```{.kotlin}
fun main() {
    var a: Int = 0

    while (a < 5) {
        println(a++)
    }
}
```

### do..while
- 최초 한 번은 **조건없이 do에서 구문을 실행**한 후 while로 조건을 체크한다
```{.kotlin}
fun main() {
    var a: Int = 0

    do {
        println(a++)
    } while (a < 5)
}
```

## 범위형 반복문
### for
- **index**를 가지고 동작한다
- 기본적으로 값을 **1씩 증가**시키며 반복한다
- **step**을 이용해 증가하는 크기를 조절할 수 있다
```{.kotlin}
fun main() {
    // for문 기본 사용법
    for(i in 0..9) {
        print(i)
    }

    // for문 step 사용법
    for (i in 0..9 step 3) {
        print(i)
    }

    // for문 downTo 사용법
    // downTo 또한 step이 적용될 수 있다
    for (i in 9 downTo 0) {
        print(i)
    }

    // for문 char도 가능
    for (i in 'a'..'e') {
        print(i)
    }
}
```

## 증감연산자 (Increment & Decrement Operator)
- 변수의 앞이나 뒤에 **++**를 붙여 변수의 값을 **'1'** 증가/감소하는 역할
### 전위 연산자 (Prefix Operator)
- **++a**/**--a**
- 연산자가 포함된 구문에서 이미 증감된 수를 반영하여 연산을 진행

### 후위 연산자 (Postfix Operator)
- **a++**/**a--**
- 증가나 감소된 수를 해당 구문에서 사용하지 않고 **'다음 구문'**에서 사용
