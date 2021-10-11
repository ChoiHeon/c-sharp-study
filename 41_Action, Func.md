# Action, Func

* Action, Func 대리자(delegate) 역할을 할 수 있습니다.



### 사용 방법

```c#
Action action1 = () => { Console.WriteLine(10); }
Action<int> action2 = (int a) => { console.WriteLine(a); }
Action<int, int> action3 = (int a, int b) =? { Console.WriteLine("{0} {1}", a, b); }
```

* `Action`은 반환값이 반드시 없어야 합니다.

```c#
Func<string> func1 = () => { return "Hello Worled!"; }
Func<string, string> func2 = (string s) => { return s + "!"; }
```

* `Func`은 반환값이 반드시 있어야 합니다.

