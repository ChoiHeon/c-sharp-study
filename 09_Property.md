# Property

속성이란 의미로서 속성 값을 반환하거나 새 값을 할당할 수 있습니다. 다음은 기본적인 Property 선언 형식입니다.

> class 클래스명 {
>
> ​	데이터타입 필드명;
>
> ​	접근한정자 데이터타입 프로퍼티명 {
>
> ​		get {
>
> ​			return 필드명;
>
> ​		}
>
> ​		set {
>
> ​			필드명 = value;
>
> ​		}
>
> ​	}
>
> }

get을 통해 필드 값을 얻을 수 있고, set을 통해 값을 변경할 수 있습니다.
반드시 둘 다 사용해야 하는 건 아닙니다. 둘 중 하나만 사용해도 됩니다.

<br>

## Example

```c#
class Student {
    private string name;
    private int age;
    
    public string Name {
        get {return name;}
        set {
            if (value.Length > 3) 
                Console.WriteLine("이름은 3자 이상을 넘길 수 없습니다.");
            else 
                name = value;
        }
    }
    
    public int Age {
        get {return age;}
        set {age = value;}
    }
}

class Program {
    public static void Main(string[] args) {
        Student student = new Student();
        
        student.Age = 13;
        student.Name = "김수한무";
        student.Name = "수한무";
    }
}
```

* 필드의 값을 얻거나 변경하는 작업을 public 으로 할 수 있습니다.