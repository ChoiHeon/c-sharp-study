# Generic

.NeET 2.0에서 새롭게 추가된 개념으로서 형식 매개변수를 사용할 수 있습니다. 형식 매개변수를 클래스나 메서드에 사용하면 인스턴스와 될 때까지 형식지정을 연기할 수 있습니다.

```c#
class MyStack<T> {
    private List<T> data;
    
    public MyStack() {
        data = new List<T>();
    }
    
    public void Push(T _value) {
        this.data.Add(_value);
    }
    
    public T Pop() {
        T ret = this.data[this.data.Count - 1];
        this.RemoveAt(this.data.Count - 1);
        return ret;
    }
    
    public int Count {
        return this.data.Count;
    }
}

class Program {
    MyStack<int> intStack = new MyStack<>();
    intStack.push(1111);
    intStack.push(2222);
}
```

<br>

## Generic의 공변과 반공변

* 변성이란?

  * 변성이란 Generic 프로그래밍을 하면서 상속에 관련되어 생기는 이슈입니다.
  * 예를 들면 Integer는 Number를 상속받아 만들어진 객체이므로, Integer는 Number의 하위 타입이라고 할 수 있습니다.
  * 하지만 List\<Integer>는 List\<Number>의 하위 타입이 될 수 없습니다.
  * 이를 통해서 아래와 같이 설명이 가능합니다.

  | 종류     | 의미                                                         |
  | -------- | ------------------------------------------------------------ |
  | 공변성   | S가 T의 서브타입, C\<S>는 C\<T>의 서브타입입니다.<br />S가 T의 서브타입, C\<S>는 C\<out T>의 서브타입입니다. |
  | 반공변성 | S가 T의 서브타입, C\<T>는 C\<S>의 서브타입입니다.<br />S가 T의 서브타입, C\<T>는 C\<in S>의 서브타입입니다 |
  | 무공변성 | C\<T>와 C\<S>는 아무 관계가 없습니다.                        |

  <br>

  위의 설명과 같이 in, out을 통해 변성을 표현할 수 있습니다.

  ```c#
  public interface IBookList<in T>
  {
      void AddBookData(T data);
      void CountIsMore(T t1, T t2);
  }
  
  public MonsterBook : IBookList<Monster>
  {
      private List<Monster> monsterBook;
      
      public void AddBookData(Monster data) {
  		monsterBook.Add(data);
          return;
      }
  }
  ```

  ```c#
  class Monster {}
  
  class MonterDragon : Monster {}
  
  class MonsterOrc : Monster {}
  ```

  ```c#
  class Program {
      IBookList<Monster> msBook = new MonsterBook();
      MonsterDragon dragon = new MonsterDragon("dragon", 1);
      MonsterOrc orc = new MonsterOrc("orc", 2);
      
      msBook.AddBookData(dragon);
      msBook.AddBookData(orc);
      
      IBookList<MonsterDragon> msBook = msBook;
  }
  ```

  * *IBookList\<MonsterDragon> msBook = msBook;*
    * 반공변성을 사용하는 코드입니다.
    * \<in T>을 사용하지 않으면 오류가 발생하는 코드입니다.

