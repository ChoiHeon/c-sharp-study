# event

특정 사건이 발생하면 알리는 역할을 합니다. 다음은 delegate를 이용한 이벤트를 처리하는 방법입니다.

> 한정자 event 델리게이트명 이벤트명;

```c#
namespace ConsoleApplication1 {
    public delegate void MyEventHandler(string message);
    
    class Publisher {
        public event MyEventHandler Active;
        
        public void DoActive(int number) {
            if (number % 10 == 0)
                Active("Active! " + number);
            else
                Console.WriteLine(number);
        }
    }
    
    class Subscriber {
        static public void MyHandler(string message) {
            Console.WriteLine(message);
        }
        
        static void Main(string[] args) {
            Publisher publisher = new Publisher();
            publisher.Active += new MyEventHandler(MyHandler);
            
            for (int i = 1; i < 30; i++)
                publisher.DoActive(i);
        }
    }
}
```

*  *publisher.Active += new MyEventHandler(MyHandler);*
  * Active 이벤트에 MyHandler 메서드를 이벤트 핸들러로 등록합니다.

<br>위의 *public event MyEventHandler Active;* 코드는 결국 delegate를 간편하게 표기하는 방법이며 콜백 패턴을 구현할 때 코드를 줄일 수 있는 장점이 있습니다.

