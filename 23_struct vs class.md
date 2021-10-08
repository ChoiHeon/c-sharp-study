# struct vs class

* `struct`와 `class`는C#에서 object 타입을 생성할 때 사용할 수 있는 키워드입니다.
* 둘 모두 필드와 메서드를 가질 수 있다는 공통점이 있습니다.

<br>

### 차이점

* `class`는 type을 정의할 때, reference 타입을 정의합니다.
  * object는 힙 메모리에 저장합니다.
  * object이 저장된 메모리는 스택에 저장됩니다.
* `struct`는 type을 정의할 때, value 타입을 정의합니다.
  * object는 스택에 저장됩니다
  * 상속할 수 없습니다.

<br>

### reference & value Type

* reference
  * class, delegate, interface로 정의할 수 있습니다.

* value

  * struct와 enum 키워드를 사용해 custom value 타입을 정의할 수 있습니다.

<br>

### 분류

* `struct`
  * Numbers: byte, sbyte, short, ushort, int, uint, ulong, float, double, decimal
  * micellaneous: char, bool
  * System.Drawing: Color, Point, Rectangle
  * Unity: Vector3
* `class`
  * 위에 언급하지 않은 대부분 타입
  * string

<br>

### 성능 비교

* 구조체와 클래스를 매개변수로 사용할 경우, 구조체는 값 형식이므로 전체를 복사합니다.
* 클래스는 단순히 참조만 하므로 클래스가 더 성능이 좋습니다.
* 하지만 크기가 작은 데이터가 많을 경우에는 구조체가 더 나을 수 있습니다.

