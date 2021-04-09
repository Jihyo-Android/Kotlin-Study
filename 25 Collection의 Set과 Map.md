# 25. Collection의 Set과 Map

## 세트 (Set)
- 순서가 없으며 **중복이 허용되지 않는** 컬렉션
- 따라서, **인덱스로 객체를 참조할 수 없으며**
- **sampleSet.contains("A")** 처럼 **contains("")** 함수로 **Set** 안에 존재하는지 확인하는 식으로만 사용
- **List**와 마찬가지로 **Set<out T>** **MutableSet<T>** 두 가지 형태

### Set 관련 함수
#### 요소의 추가
- add(데이터)

#### 삭제
- remove(데이터)

```kotlin
fun main() {
    val a = mutableSetOf("귤", "바나나", "키위")

    for (item in a) {
        println("${item}")
    }

    a.add("자몽")
    println(a)

    a.remove("바나나")
    println(a)

    println(a.contains("귤"))
}
```

## 맵 (Map)
- 객체를 넣을 때 그 객체를 찾아낼 수 있는 **Key**를 쌍으로 넣어주는 컬렉션
- **key** : 객체를 찾기위한 값
- **value** : key와 연결된 객체
- 내부적으로 **MutableMap.MutableEntry**에 객체로 담겨져 있으며 이런 구조로 객체의 위치가 아닌 **고유한 key**를 통해 객체를 참조
- **같은 key**에 **다른 객체**를 넣으면 기존의 객체가 **대체**되니 주의
- 다른 컬렉션과 마찬가지로 **Map<K, out V>**, **MutableMap<K, V>** 두 가지 형태

### Map 관련 함수
#### 요소의 추가
- put(키, 값)

#### 삭제
- remove(키)

```kotlin
fun main() {
    val a = mutableMapOf("레드벨벳" to "음파음파",
                        "트와이스" to "FANCY",
                        "ITZY" to "ICY")
    for (entry in a) {
        println("${entry.key}" : ${entry.value}")
    }

    a.put("오마이걸", "번지")
    println(a)

    a.remove("ITZY")
    println(a)

    println(a["레드벨벳"])
}
```
