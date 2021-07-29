# Task

* 스레드에서 반환하는 결과만 필요한 경우 비동기 프로그래밍을 사용하는 것이 좋습니다.
* C#에서는 Task를 이용해 효율적으로 비동기 프로그래밍을 구현할 수 있습니다.
* .NET 4.0에 도입된 클래스입니다.
  * Task 이전의 ThreadPool, QueueUserWorkItem보다 빠르고 유연한 기능을 갖습니다.
* 스레드풀에서 스레드를 가져와 비동기 작업을 실행시킵니다.
* Task.Factory.StartNew()를 통해 실행하고자 하는 함수에 대한 델리게이트를 지정할 수 있습니다.
  * 스레드의 생성과 동시에 실행하는 방식입니다.
  * 생성만 하려면 Task() 생성자를 사용합니다.

<br>

```c#
namespace MultiApp
{
    using System;
    using System.Threading.Task;
    
    class Program
    {
        static void Main(string[] args)
        {
            // Task.Factory.StartNew 사용
            Task.Factory.StartNew(new Action<object>(Run), null);
            Task.Factory.StartNew(new Action<object>(Run), "1st");
            Task.Factory.StartNew(Run, "2nd");
            
            // Task 생성자 사용
            Task t1 = new Task(new Action(Run));
            Task t2 = new Task(() => {
                Console.WriteLine("Do something");
            })
            
            t1.Start();
            t2.Start();
            
            t1.Wait();
            t
        }
        
        static void Run(object data)
        {
            Console.WriteLine(data == null ? "NULL" : data);
        }
    }
}
```

