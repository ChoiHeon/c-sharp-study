# LINQ를 이용한 집합

* LINQ를 이용해서 집합 연산을 할 수 있습니다.
* 집합 연산이란 중복 제거, 차집합, 합집합 연산을 의미합니다.

<br>

### 중복 제거 (Distinct)

* 질의의 결과에서 중복을 제거합니다.

  ```c#
  List<int> numbers = new List<int>() { .. };
  var result = (from n in numbers where n % 2 == 1 select n).Distinct();
  
  foreach(int a in result) 
      Console.Write(a + ", ");
  
  // numbers.Dinstinct();를 호출해도 같은 결과를 얻을 수 있습니다.
  ```

<br>

### 차집합 (Except)

```c#
List<int> numbers = new List<int>() { .. };
var result = (from n in numbers where n % 2 == 1 select n)
    		.Except(from n in numbers where n % 4 == 0 select n);
```

* 2의 배수 중 4의 배수를 제외합니다.

<br>

### 교집합 (Intersect)

```c#
List<int> numbers = new List<int>() { .. };
var result = (from n in numbers where n % 2 == 1 select n)
    		.Intersect(from n in numbers where n % 3 == 0 select n);
```

* 2의 배수와 3의 배수의 교집합을 구합니다.

<br>

### 합집합 (Union)

```c#
List<int> numbers = new List<int>() { .. };
var result = (from n in numbers where n % 2 == 1 select n)
    		.Union(from n in numbers where n % 3 == 0 select n);
```

* 2의 배수와 3의 배수의 합집합을 구합니다.

