# 링크 (LINQ)

* 통합된 질의 언어로 Language-Integrated Query의 약자입니다.
* C# 3.0부터 추가가 되었습니다.
* 링크를 통해서 컬렉션 형태를 띄는 모든 데이터에 질의를 할 수 있습니다.
* 가장 많이 사용하는 문법은 다음과 같습니다.
  * from
  * where
  * order by
  * select

<br>

###  from

> from 범위 변수 in 범위 데이터

* 어떤 데이터에서 찾을 것인지를 의미합니다.
* foreach와 기능이 유사합니다.
  * foreach와는 다르게 범위 변수에 실제로 데이터를 저장하지 않습니다.
  * 범위 데이터는 IEnumerable 또는 IEnumerable\<T>를 상속받거나
  * IQueryable\<T>와 같은 파생 인터페이스를 지원해야 합니다.
* 배열도 적용이 가능합니다.

<br>

### where

> where 조건식

* 조건식을 이용한 필터 같은 역할을 할 수 있습니다.
* 범위 데이터의 각 요소에 대해 조건식을 적용, 참인 경우에만 해당 요소를 반환합니다.

<br>

### orderby

> orderby 정렬 기준 (asending 또는 descending)

* 정렬 기준을 바탕으로 정렬한 결과를 반환합니다.
* 기본적으로 오름차순(asending) 정렬을 합니다.
* 내림차순은 desending을 추가하면 됩니다.

<br>

### select

> select 원하는 요소

* 최종적인 결과를 도출해내는 역할을 합니다.
* LINQ 쿼리는 from으로 시작해 select 절 또는 gorup 절로 끝나야 합니다.

<br>

### group

> group A by B into C

* A는 범위 변수, B는 분류 기준, C는 그룹 변수를 의미합니다.
* 추가적인 쿼리문을 수행하지 않을 경우 into 키워드를 생락할 수 있습니다.

<br>

### Example

```c#
int[] numbers = { 1, 3, 4, 6, 5, 9, 8, 12, 15, 18, 17, 11, 22 }; 
var data =  from num in numbers 
    	   	where num < 10 && num % 2 == 0 
    	   	orderby num 
    		select num;
```

* 배열의 원소 중 10 미만, 짝수인 값만 오름차순으로 정렬해 반환합니다.

<br>

```c#
List<Student> listStudent = new List<Student> {
    new Student() {Name = "김철수", Average = 78.5},
    new Student() {Name = "김영희", Average = 91.2},
    new Student() {Name = "홍길동", Average = 77.3},
    new Student() {Name = "김길수", Average = 80.8},
};

var queryStudent = 	from student in listStudent
    				orderby student.Average
    				group student by student.Average < 80.0;

foreach(var studentGroup in queryStudent) {
    Console.WriteLine(studentGroup.Key ? "평균 80점 미만:" : "평균 80점 이상:");
    
   	foreach(var student in studentGroup)
        Console.WriteLine("\t{0}: {1}점", student.Name, student.Average);
}
```

* group절의 조건 결과를 key 값으로한 Dictionary 객체를 LINQ의 결과로 반환합니다.
* 따라서 key 값이 bool 형으로 정해집니다.

