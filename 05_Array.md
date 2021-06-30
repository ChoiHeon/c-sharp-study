# 배열

기본적인 배열 선언 및 다중 배열 선언에 대한 내용입니다.

<br>

## 1차원 배열

```c#
int[] arr1 = new int[6];

int[] arr2 = new int[6] {0, 1, 2, 3, 4, 5};

int[] arr3 = {0, 1, 2, 3, 4, 5};

int[] arr4 = new int[] {0, 1, 2, 3, 4, 5};
```

<br>

## System.Array

배열을 만들고, 조작하고, 검색 및 정렬하여 CLR에서 모든 배열의 역할을 수행하도록 메서드를 제공합니다.

| 속성   | **기능**                     |
| ------ | ---------------------------- |
| Rank   | 배열의 차원 수를 반환합니다. |
| Length | 배열의 길이를 반환합니다.    |

| 메소드  | 기능                                                         |
| ------- | ------------------------------------------------------------ |
| Clear   | 원소의 자료형이 정수일 경우 0, 논리일 경우 false, <br />참조형일 경우 null로 초기화합니다. |
| ForEach | 지정한 배열의 각 요소에서 지정한 동작을 수행합니다.          |
| Resize  | 뱌욜의 요소 수를 지정된 새로운 크기로 변경합니다.            |
| indexOf | 지정된 개체를 검색, 첫 번째로 발견한 개체의 인덱스를 반환합니다. |

```C#
using System;

namespace ConsoleApplicaion1 {
    class Program {
        static void Main(string[] args) {
            int[] arr = new int[] {1, 2, 3, 4, 5, 6};
            
            Console.WriteLine(arr.Rank);
            Console.WriteLine(arr.Length);
            Console.WriteLine(Array.indexOf(arr, 4));
            
            Array.Clear(arr, 0, 6);
            
            Array.Resize(ref arr, arr.Length + 3);
            
            Array.ForEach<int>(arr, new Action<int>(ShowValue));
            
            
        }
        
        static void ShowValue(int value) {
            Console.WriteLine("{0}", value);
        }
    }
}
```

<br>

## 다차원 배열

```c#
int[,] arr = new int[3, 6];	
int[,,] arr2 = new int[3, 6, 8];
```

