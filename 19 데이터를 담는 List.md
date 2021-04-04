# 19. 데이터를 담는 List

## 리스트 (List)
- **Collection** 클래스를 상속받는 클래스 **Set**, **Map**과 같은 서브 클래스이다
- 여러 개의 데이터를 원하는 순서로 넣어 관리한다
- **List<out T>**, **MutableList<T>** 두 가지 형태가 있다

### List<out T>
- 생성 시에 넣은 객체를 대체, 추가, 삭제할 수 없음

### MutableList<T>
- 생성 시에 넣은 객체를 대체, 추가, 삭제가 가능함

### 리스트 생성
```kotlin
listOf(1, 2, 3)
mutableListOf("A", "B", "C")
```

### 리스트 관련 함수
#### 요소의 추가
- add(데이터)
- add(인덱스, 데이터)

#### 삭제
- remove(데이터)
- removeAt(인덱스)

#### 무작위 섞기
- shuffle()

#### 정렬
- sort()

```kotlin
fun main() {
    val a = listOf("사과", "딸기", "배")
    println(a[1])

    for(fruit in a) {
        println("${fruit} : ")
    }

    println()

    val b = mutableListOf(6, 3, 1)
    println(b)

    b.add(4)
    println(b)

    b.add(2, 8)
    println(b)

    b.removeAt(1)
    println(b)

    b.shuffle()
    println(b)

    b.sort()
    println(b)
}
```