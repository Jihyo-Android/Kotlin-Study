# 27. Collection 함수 (2)

## Collection 함수
### name과 birthYear로 이루어진 collection 
- **collection.associateBy{ it.name }** : 아이템에서 **key**를 추출하여 **map**으로 변환
- **collection.groupBy{ it.birthYear }** : key가 같은 아이템끼리 배열로 묶어 **map**을 만듦
- **collection.partition{ it.birthYear > 2002 }** : 아이템에 **조건**을 두어 두 개의 collection으로 나누어 **Pair**라는 클래스 객체로 반환하며 각 collection을 **first**, **second**로 참조하여 사용 가능

```kotlin
fun main() {
    data class Person(val name: String, val birthYear: Int)

    val personList = listOf(Person("유나", 1992),
                            Person("조이", 1996),
                            Person("츄", 1999),
                            Person("유나", 2003))
    
    println(personList.associateBy{ it.birthYear })
    println(personList.groupBy{ it.name })

    val (over98, under98) = personList.partition{ it.birthYear > 1998 }
    println()
    println(under98)
}
```

- **collection.flatMap{ listOf(it*3, it+3) }** : 아이템마다 만들어진 collection을 합쳐서 반환
- **collection.getOrElse(1){ 50 }** : 소괄호 안에 인덱스 위치에 아이템이 있으면 아이템을 반환하고 아닌 경우 중괄호 안에 지정한 기본값을 반환
- **collectionA zip collectionB** : collection 두 개의 아이템을 **1:1**로 **Pair** 클래스의 객체로 만들어 **List**에 넣어 반환. 이 때, **결과 List**의 아이템의 개수는 **더 작은 collection**을 따라감

```kotlin
fun main() {
    val number = listOf(-3, 7, 2, -10, 1)

    println(numbers.flatMap{ listOf(it*10, it+10) })

    println(numbers.getOrElse(1){ 50 })
    println(numbers.getOrElse(10){ 50 })

    val names = listOf("A", "B", "C", "D")

    println(names zip numbers)
}
```
