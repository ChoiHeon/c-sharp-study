# LINQ를 이용한 요소 탐색

* System.Linq에는 배열의 탐색을 위해 정의된 메서드가 존재합니다.

<br>

### 일반적인 LINQ 사용

```c#
int[] array = { -1, 1, 2, -2, 3 };

int target = from e in array where e < 0 select e;
```

<br>

### First

* 주어진 조건과 일치하는 첫 번째 요소를 반환합니다.

```c#
int[] array = { -1, 1, 2, -2, 3 };

int target = array.First(e => e < 0);
```

<br>

### FirstOrDefault

* 주어진 조건과 일치하는 젓 번째 요소를 반환합니다.
* 만약 일치하는 요소가 없을 경우, 해당 타입의 디폴트 값을 반환합니다.

```c#
int[] array = { -1, 1, 2, -2, 3 };

int target = array.FirstOrDefault(e => e < 0);
```

<br>

### Where

* 조건과 일치하는 요소들을 담은 컬렉션을 반환합니다.
  * 반환하는 컬렉션의 종류는 메서드를 호출한 컬렉션과 일치합니다.

```c#
int[] array = { -1, 1, 2, -2, 3 };

int[] sub = array.Where(e => e < 0); // sub = { -1, -2 }
```

<br>

### ElementAt

* 컬렉션에서 인자로 넣은 인덱스의 요소를 반환합니다.

```c#
int[] array = { -1, 1, 2, -2, 3 };

int target = array.Where(e => e < 0).ElementAt(1); // target = -2
```

<br>

### OfType

* 컬렉션에서 해당 타입과 일치하는 요소들을 담은 컬렉션을 반환합니다.

```c#
List<Pet> pets = new List<Pet>();

pets.Add(new Dog() {Nane = "AAA"});
pets.Add(new Dog() {Nane = "BBB"});
pets.Add(new Cat() {Nane = "CCC"});
pets.Add(new Rabbit() {Nane = "DDD"});

var dogs = pets.OfType<Dog>();
```

<br>

### All

* 컬렉션의 모든 요소가  조건을 만족하는지를 반환합니다.

```c#
bool check = array.All(e => e >= 1000); // 모든 요소가 1000 이상인지 확인
```

<br>

### Any

* 컬렉션의 임의의 요소가 조건을 만족하는지를 반환합니다.

```c#
bool check = array.Any(e = e >= 1000); // 임의의 요소가 1000 이상인지 확인
```

<br>

### Contains

* 컬렉션의 요소 중에 해당 값을 가지고 있는지를 반환합니다.

```c#
bool check = array.Contains(5); // 요소 중에 5가 있는지 확인
```

<br>

### Select

* 원하는 값을 가져올 수 있습니다.

```c#
List<int> numbers = new List<int>() {1, 2, 3, 4, 5, 6, 7};
var result = numbers.Select((v, idx) =>
                            {
                                if (idx % 2 == 0) return v * 2;
                                else return v;
                            }); // * 인덱스가 짝수일 경우 제곱수인 컬렉션을 반환합니다.


```

<br>

* 무명 객체를 생성할 수 있습니다.

```c#
List<Person> people = new List<Person>();
people.Add(new Person() {Name = "AAA", ID = 1});
people.Add(new Person() {Name = "BBB", ID = 2});
people.Add(new Person() {Name = "CCC", ID = 3});
people.Add(new Person() {Name = "CCC", ID = 4});

var result = from p in people select new { p.Name }; // Name을 프로퍼티로 갖는 무명 객체를 요소로 가집니다.

foreach (var p in result) {
    Console.Write(p.Name + ", ");
}
```

<br>

### SelectMany

* 컬렉션의 요소가 또 다른 컬렉션인 경우 from을 연속으로 사용해서 접근할 수 있습니다.

```c#
List<Merchant> merchants = new List<Merchant>() {
    new Merchant {items = new List<string> {"Apple", "Orange"}},
    new Merchant {items = new List<string> {"Pencil", "ruler"}},
    new Merchant {items = new List<string> {"Gun", "Knife"}}
};

var result = 	from merchant in merchants
    			from item in merchant.items
    			select item;

foreach(var e in result)
    Console.Write(e + ", ");
```

<br>

* 위의 코드를 SelectMany 함수를 이용해서 구현할 수 있습니다.

```c#
List<Merchant> merchants = new List<Merchant>() {
    new Merchant {items = new List<string> {"Apple", "Orange"}},
    new Merchant {items = new List<string> {"Pencil", "ruler"}},
    new Merchant {items = new List<string> {"Gun", "Knife"}}
};

var result = merchants.SelectMany(m => m.items);

foreach(var e in result)
    Console.Write(e + ", ");
```

<br>

### Skip

* Partitioaning에 필요한 함수입니다.
* 입력한 숫자만큼 요소를 스킵한 컬렉션을 반환합니다.

```c#
int[] array = { 1, 2, 3, 4, 5 };

var result = array.Skip(3); // { 4, 5 }
```

<br>

### Take

* Partitionaing에 필요한 함수입니다.
* 컬렉션의 맨 앞부터 입력한 값 만큼의 개수의 요소들을 반환합니다.

```c#
int[] array = { 1, 2, 3, 4, 5 };

var result = array.Take(3); // { 1, 2, 3 }
var result2 = array.Skip(2).Take(2); // { 3, 4 }
```

<br>

### SkipWhile

* 입력한 조건이 만족하지 않을 떄까지 요소를 스킵합니다.

```c#
int[] array = { 1, 2, 3, 4, 5 };

var result = array.SkipWhile(e => e < 3); // { 3, 4, 5 }
```

<br>

### TakeWhile

* 입력한 조건을 만족하는 연속된 요소들만 반환합니다.

```c#
int[] array = { 1, 2, 3, 4, 5 };

var result = array.TakeWhile(e => e < 3); // { 1, 2 }
```

