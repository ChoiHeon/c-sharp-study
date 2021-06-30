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



