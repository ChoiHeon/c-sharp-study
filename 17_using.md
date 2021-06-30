# using

C#에서 `using`은 여러 의미로 사용됩니다.

<br>

## 지시문 using

* 네임스페이스에 정의된 각 타입을 참조할 때 사용합니다.

```c#
using System;
using System.Collections.Generic;
```

<br>

## 문장 형태 using

* IDispoable 객체의 올바른 사용을 보장하는 편리한 구문을 제공합니다.
  *  관리되지 않는 리소스(ex. Feile, Font, ...)를 사용한 후 해제하여 리소스를 반납해야 합니다.
  * 이 때, 프로그래머스 매번 해제를 하는 것은 문제를 야기할 수 있으므로 `using`을 사용해 자동으로 자원을 해제하도록 하는 것이 좋습니다.
* 다음의 경우 Dispose() 를 호출합니다.
  * using 구문이 정상적으로 종료됐을 때
  * using 구문 내에서 에러가 발생했을 때
* try ~ finally와 기능은 동일하지만, using이 더 빨리 읽힙니다.

<br>

1. `using `을 사용하지 않을 경우

   ```c#
   Font font = new Font("Arial", 10.0f);
   
   try 
   {
   	byte charset = font.GdiCharSet;    
   }
   finally 
   {
       if (font != null)
           ((IDisponsable)font).Dispose();
   }
   ```
   
   <br>

2. `using `을 사용할 경우

    ```c#
    using (Font font = new Font("Arial", 10.0f))
    {
        byte charset = font.GdiCbarSet;
    }
    ```

