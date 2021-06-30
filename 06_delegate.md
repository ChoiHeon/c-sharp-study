# delegate

델리게이트는 일종의 대리자라고 할 수 있습니다. 메서드를 참조하는 등의 대리자 역할이 가능합니다.

> delegate 반환형 델리게이트명 (매개변수...);

델리게이트는 위와 같은 매개변수, 반환형이 일치하는 메서드를 가리킬 수 있습니다.

<br>

## Exmaple

```C#
using System;

namespace ConsoleApplication1 {
    delegate int PDelegate(int a, int b);
    
    class Program {
		static int Plus(int a, int b){
            return a + b;
        }
        
        static void Main(stirng[] args) {
            PDelegate pd1 = Plus;
            PDelegate pd2 = delegate(int a, int b) {
                return a / b;
            };
            
            Console.WriteLine(pd1(5, 10));
            Console.WriteLine(pd2(50, 10));
        }
    }
}
```

<br>

## delegaet chain

```c#
using System;

namespace ConsoleApplication1 {
    delegate int PDeleagate(int a, int b);
    
    class Program {
        static void Plus(int a, int b) {
            Console.WriteLine(a + b);
        }
        
        static void Minus(int a, int b) {
            Console.WriteLine(a - b);
        }
        
        static void Multi(int a, int b) {
            Console.WriteLine(a * b);
        }
        
        static void Main(string[] args) {
            PDelegate pd = (PDelegate)Delegate.Combine(new PDelegate(Plus), 
                                                       new PDelegate(Minus),
                                                       new PDelegate(Multi)
                                                       );
            pd(20, 10);
        }
    }
}
```

```
// output
30
10
200
```

* *(PDelegate)Delegate.Combine(...);*
  * delegate 객체들을 몪습니다.
  * 각 객체는 같은 인자 갯수, 타입, 반환 타입의 함수를 인자로 생성됩니다.
  * 묶은 delegate를 형변환합니다.