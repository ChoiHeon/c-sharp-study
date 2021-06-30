# Attribute

Java의 annotation과 유사한 문법. 내장되어 있는 공통 Attribute나 사용자가 정의한 커스텀 Attribute로 나뉘며, 공통 Attribute는 컴파일 방식에 영향을 줄 수 있습니다.

다음은 공통 Attribute의 일부입니다.

* Consditional
* Obsolute
* DllImport 

<br>

## Conditional

메소드에만 정용할 수 있는 Attribute입니다. #define 전처리로 정의되었는지 여부에 따라 메소드 컴파일 여부를 결정합니다.

```c#
#define TEST
    
namespace ConsoleApplication1 {
    class Program {
        [Conditional("TEST")]
        public void Conditional() {
            Console.WriteLine("Test Conditional");
        }
        
       	static void Main(String[] args) {
            Program program = new Program();
            
            program.TestConditional();
        }
    }
}
```

```
// output
Test Conditional
```

* 만약 *#define TEST*가 생략되었다면 아무것도 출력되지 않습니다.

<br>

## Obsolute

클래스내에서 더 이상 사용되지 않는 메서드를 사용하려 할 때, 사용을 하지 말라는 문구를 출력하고 경고 또는 에어를 발생시킵니다.

```c#
namespace ConsoleApplication1 {
    class Program {
        [Obsolute("OldMethod()는 더 이상 사용하지 않으므로, NewMethod()를 사용해주세요.")]
      	public void OldMethod() {
            Console.WriteLine("OLD");
        }
        
        public void NewMethod() {
            Console.WriteLine("NEW");
        }
        
        public static void Main(string[] args) {
            Program program = new Program();
            
            program.OldMethod();
            program.NewMethod();
        }
    }
}
```

```
// output
OLD
NEW

// warning
OldMethod()는 더 이상 사용하지 않으므로, NewMethod()를 사용해주세요.
```

* Obsolute의 두 번째 인자로 true를 넣으면, 해당 메서드를 더 이상 사용하지 않는다는 에러를 발생시킵니다.
  * *[Obsolute("error-message", true)]*

<br>

## DllImport

외부 라이브러리를 사용합니다. 프로그램의 외부를 의미하는 extern 키워드를 붙여야 합니다.

```c#
using System.Runtime.InteropServices;

namespace ConsoleApplication {
    class Program {
        [DllImport("User32.dll")]
        public static extern int MessageBox(int hParent, string Message, string Caption, int type);
        
        static void Main(string[] args) {
            MessageBos(0, "DllImport!", "Dllimport", 3);
        }
    }
}
```

<br>

## 사용자 정의 Attribute

System.Attribute 클래스를 상속함으로써 직접 Attribute의 정의가 가능합니다.

``` c#
namespace ConsoleApplication {
    
    class CustomAttribute : System.Attribute {
        private string str;
        private string tmp;
        
        public CustomAttribute(string str) {this.str = str;}
        public string vartmp {
            get {return tmp;}
            set (this.tmp = value;)
        }
    }
    
    [CustomAttribute("STR", vartmp="TMP")]
    class Program {
        static void Main(string[] args) {
            C
        }
    }
}
```



