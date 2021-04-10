# 26. Collection 함수 (1)

## Collection 함수
List, Set, Map과 같은 **컬렉션** 또는 **배열**에 일반 함수 또는 람다 함수 형태를 사용하여 **for**문 없이 아이템을 참조하거나, 조건을 걸고 구조의 변경까지 가능한 여러가지 함수를 지칭한다

### Collection first, last 함수
#### first, last 일반 함수
- **collection.first()** : collection의 첫 번째 아이템 반환
- **collection.last()** : collection의 마지막 아이템 반환

#### first, last 람다 함수
- **collection.first{}** : 조건에 맞는 첫 번째 아이템 반환. **find**로 대체 가능
- **collection.last{}** : 조건에 맞는 마지막 아이템을 반환. **findLast**로 대체 가능

### NoSuchElementExcetpion
- **first**와 **last** 함수 사용시 발생할 수 있는 문제
- 조건에 맞는 객체가 없는 경우(= collection이 비어있는 경우)
- **firstOrNull**이나 **lastOrNull**을 사용하여 객체가 없는 경우 **null**을 반환

### Collection 람다 함수
- **collection.forEach{}** : collection에 포함된 모든 아이템을 순서대로 **it**이라는 변수로 참조
- **collection.filter{}** : **it**에 조건을 걸어주면 조건에 맞는 객체만 collection으로 반환
- **collection.map{}** : **it**에 수식을 적용한 값을 컬렉션으로 반환 
- **collection.any{}** : 하나라도 조건에 맞으면 true
- **collection.all{}** : 모두 조건에 맞으면 true
- **collection.none{}** : 하나라도 조건에 맞으면 true 

### count 일반 함수와 람다함수
- **collection.count()** : collection의 모든 아이템의 개수 반환
- **collection.count{}** : 조건에 맞는 아이템의 개수 반환

```kotlin
fun main() {
    val nameList = listOf("박수영", "김지수", "김다현", "신유나", "김지우")

    nameList.forEach{ print(it + " ") }
    println()

    println(nameList.filter{ it.startsWith("김") })

    println(nameList.map{ "이름 : " + it })

    println(nameList.any{ it == "김지연" })
    println(nameList.all{ it.length == 3 })
    println(nameList.none{ it.startsWith("이") })

    println(nameList.first{ it.startsWith("김") })
    println(nameList.last{ it.startsWith("김") })
    println(nameList.count{ it.contains("지") })
}
```
