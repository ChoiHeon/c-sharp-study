# Generic Collection

System.Collections.Generic 네임스페이스엔 제네릭을 사용하는 자료구조가 정의되어 있습니다.

* Dictionary<Key, Value>
* HashSet\<Key>
* LinkedList\<T>
* List\<T>
* Queue\<T>
* SortedDictionary<Key, Value>
* SortedList<Key, Value>
* SortedSet\<T>
* Stack\<T>

<br>

## Array vs ArrayList vs List

| Array                                                        | ArrayList                                                    | List                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 고정된 배열 크기를 갖습니다(변형이 불가합니다).<br />같은 타입만 저장가능합니다.<br />다차원 비열 입력이 가능합니다. | 고정되지 않는, 추가/삭제의 변형이 가능합니다.<br />제네릭 타입으로서 서로 다른 타입의 데이터의 저장이 가능합니다.<br />데이터를 가져올 때 박싱, 언박싱이 발생해 type=safe하지 못한 이슈가 있습니다. | ArrayList 처럼 고정되지 않는 가변 객체입니다.<br />ArrayList의 단점을 보완하고자 컴파일시 배열의 타입을 추론합니다.<br />즉, 같은 타입만 저장이 가능합니다. |

참고로 List는 C++의 vector와 비슷한 구조입니다. capacity를 가지며 현재 가진 데이터 개수에 따라 resize를 한다는 점까지 유사합니다.

LinkedList는 List와는 달리 임의의 원소에 대한 접근의 시간복잡도가 O(N)입니다.