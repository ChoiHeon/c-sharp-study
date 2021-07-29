# async & await

* 비동기 프로그래밍을 사용하기 위한 키워드입니다.
  * 비동기 프로그래밍은 스레드에 묶이지 않고도 I/O에 한정되는 동시성을 구현할 수 있습니다.
  * 
  * C#은 콜백을 조작하거나 비동기를 지원하는 라이브러리를 따를 필요 없이 TAP(작업 기반 비동기 패턴)을 이용해 쉽게 비동기 프로그래밍이 가능합니다.

<br>

### Example

**[Task를 이용한 비동기 프로그래밍]**

```c#
using System;
using System.Threading;
using System.Threading.Task;

class Program 
{
    class countDownWrapper
    {
        public AutoResetEvent Done = new AutoResetEvent(false);
        public int count = 9;
        public void CountDown() 
        {
            Console.WriteLine(count--);
            if (count >= 0)
                Task.Delay(1000).ContinueWith((c)=>
                                              {
                                                  CountDown();
                                              });
           	else
                Done.Set();
        }
    }
    
    static void Main(string[] args) 
    {
        var a = new countDownWrapper();
        var b = new countDownWrapper();
        
        a.CountDown();
        b.CountDown();
        
        AutoResetEvent.WaitAll(new[] {a.Done, b.Done})
    }
}
```

<br>

**[async & await 사용]**

```c#
using System;
using System.Threading.Task;

class Program
{
    private static async Task countDown()
    {
        for (int i = 9; i >= 0; i--)
        {
            Console.WriteLine(i);
            await Task.Delay(1000);
        }
    }
    
    static void main(string[] args)
    {
        var a = countDown();
        var b = countDown();
        
        Task.WaitAll(a, b);
    }
}
```

* 실제로 for문을 수행하지 않지만 결과는 마치 for문을 수행한 것처럼 나오게 됩니다.
  * 이러한 구문을 신택스 슈거(syntax sugar)라고 합니다.
  * 겉으로 보이는 코드와 실제 생성되는 코드는 다르지만, 코드에 대한 이해도를 높일 수 있습니다.

