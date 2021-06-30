# Nullable

C#은 기본적으로 참조형을 제외한 타입에서는 null을 저장할 수 없습니다. 하지만 `Nullable`을 사용하면 null의 저장이 가능해집니다.

<br>

## 사용법

``` C#
Nullable<int> a = null;
// int? a = null;

if (a.HasValue)
    Console.WriteLine(a)
else
    Console.WriteLine("is null");
```

```
// expected output
is null
```

* null을 허용하고 싶은 타입명을 Nullable에 지정하거나 타입명 뒤에 `?`을 붙여서 사용할 수 있습니다.
* 해당 변수에 null 값의 저장 여부를 알려면 다음 속성 및 메서드를 사용하면 됩니다.
  * HasValue: null이 저장 여부를 bool 타입으로 반환합니다.
  * Value: 저장된 값을 반환합니다. 값이 null이라면 에러를 발생시킵니다.
  * GetValueOrDefault(): 



