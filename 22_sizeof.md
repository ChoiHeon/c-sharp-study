# sizeof

* 기본 타입의 크기는 `sizeof` 메서드를 통해서 확인할 수 있습니다.

  ```c#
  Console.WriteLine(sizeof(int)); // output: 4
  Console.WriteLine(sizeof(double)); // output: 8
  ```

* 외에도 비관리 타입의 경우 unsafe 블록에서 실행해야 합니다.

* struct나 class의 경우 ` Marshal.SizeOf`를 사용해서 알 수 있습니다.

  * 이 때, 참조형 멤버 필드가 없어야 합니다.

  ```c#
  using System.Runtime.InteropServices;
  
  struct MyStruct
  {
      public int i;     // 4 byte
      public double d;  // 8 byte
      public byte b;    // 1 byte
  }
  
  Console.WriteLine(Marshal.SizeOf(typeof(MyStruct))); // output: 24
  ```

  * 13 대신 24를 출력합니다.

<br>

### 정확한 크기를 얻는 법

* 위에서 24를 반환하는 이유는 메모리의 팩(Pack)이 8 byte 단위이기 때문입니다.

* 즉, 각 변수마다 8 byte를 할당했음을 의미합니다.

  * 변수 개수 = 3 
  * 24 = 8 * 3

<br>

* 따라서 정확한 크기를 얻기 위해선 1 byte로 정렬할 필요가 있습니다.

```c#
using System.Runtime.InteropServices;

[StructLayout(LayoutKind.Sequential, Pack = 1)]
struct MyStruct
{
    public int i;     // 4 byte
    public double d;  // 8 byte
    public byte b;    // 1 byte
}

Console.WriteLine(Marshal.SizeOf(typeof(MyStruct))); // output: 13
```

<br>

##### 참고

https://www.csharpstudy.com/DevNote/Article/10