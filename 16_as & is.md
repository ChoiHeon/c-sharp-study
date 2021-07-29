# as & is

각각 캐스팅 성공 유무를 반환하는 연산자입니다. as는 캐스팅의 결과를 반환하지만, is는 캐스팅의 유무를 true/false로 반환합니다.

<br>

```c#
class Program {
    class Parent {}
    
    class Children : Parent {
        public void Method() {
            Console.WriteLine("캐스팅 성공");
        }
    }
    
   	static void Main(string[] args) {
        Parent parent = new Parent();
        Parent parent2 = new Children();
        
        Children children = new Children();
        
        children = parent as Children;
        if (children != null) 
            children.Method();
        
        children = parent2 as Children;
        if (children != null)
            children.Method();
        
        if (parent is Children)
            Console.WriteLine("parent is Children");
        if (parent2 is Children) 
            Console.WriteLine("parent2 is Children");
    }
}
```

<br>

### as와 괄호를 이용한 캐스팅의 차이

* 괄호를 이용해서 캐스팅을 하는 경우 컴파일 과정에서 `InvalidCastException`이 발생할 수 있습니다.
* `as`를 이용하면 캐스팅에 실패할 경우 `null`을 반환합니다.

