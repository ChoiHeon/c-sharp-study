# Collection

Collection은 데이터의 검색과 저장을 위해 특화된 자료구조를 의미합니다.

<br>

## ArrayList

배열과 비슷하면서 크기가 동적인 자료구조입니다. Add, BinarySearch, Clear, Contain, Insert, Remove, Sort 등의 메서드를 지원합니다.

* Add(value)
  * 인자를 ArrayList의 맨 뒤에 추가합니다.
* BinarySearch(start, end, value, IComparer)
  * 주어진 범위내에서 주어진 비교연산자를 통해 정렬한 배열에서 이진 탐색을 통해 value를 찾습니다.
  * 찾은 value의 인덱스를 반환합니다.
  * value만 인자로 넣을 경우, 전체 범위에 대해 기본 비교연산자를 통한 이진 탐색을 수행합니다.
* Remove(index)
  * 인자로 넣은 인덱스가 가리키는 원소를 삭제합니다.
* Insert(index, value)
  * index에 value를 삽입합니다.
* Clear()
  * 모든 원소를 삭제합니다.

```c#
using System;
using System.Collection;

namespace ConsoleApplication {
    class Program {
        static void ShowArray(ArrayList list) {
            foreach(object obj in list)
                Console.Write("{0} ", obj);
            Console.WriteLine();
        }
    	
    	static void Main(string[] args) {
            ArrayList alist = new ArrayList();
            
            for (int i = 0; i < 10; i++)
                alist.Add(i);
            
            Console.Write("Alist: ");
            ShowArray(alist);
            
            
        }
    }
}
```

<br>

## Hashtable

키와 값 쌍을 원소로 갖는 자료구조로 빠른 검색을 목적으로최적화되어 있습니다. 키의 중복은 허용하지 않으며 이 때 해쉬값을 사용합니다.

```c#
// 생략

namespace ConsoleApplication {
    class Program {
        static void Main(string[] args) {
            Hashtable table = new Hashtable();
            
            table.Add("사과", "apple");  // 키: "사과", 값: "apple"
            table.Add("토마토", "tomato");
            table["감자"] = "potato";
            
            foreach(object obj in table.Keys)
                Console.WriteLine("{0}: {1}", obj, table[obj]);
        }
    }
}
```

<br>

## Queue

```c#
// 생략

namespace ConsoleApplication {
    class Program {
        static void Main(string[] args) {
            Queue queue = new Queue();
            
            queue.Enqueue("one");
            queue.Enqueue("two");
            
            while(queue.Count > 0)
                Console.WriteLine("Dequeue: {0}, Count: {1}", 
                                 queue.Dequeue(), queue.Count);
        }
    }
}
```

<br>

## Stack

```c#
// 생략

namespace ConsoleApplication {
    class Program {
        static void Main(string[] args) {
            Stack book = new Stack();
            
            book.Push("거침없이 배우는 Unity 3D");
            book.Push("강행돌파! 입문자를 위한 아이폰 & 아이패트 앱 개발");
            
            while (book.Count > 0)
                Console.WriteLine(book.P
        }
    }
}
```



