# for vs foreach

`for`와 `foreach`는 다음 코드에서 별 차이점을 보이지 않습니다.

``` C#
int[] a = { 0, 1, 2, 3, 4 }

// 1. for
for (int i = 0; i < a.Length; i++) 
    Console.WriteLine(a[i]);

// 2. foreach
foreach (var e in a)
    Console.WriteLine(e);
```

* 소스 코드와 시간적인 측면에서 큰 차이를 보이지 않습니다.

<br>

## 차이점

하지만 위의 코드처럼 배열이 아닌 다른 처리 대상에 대해선 큰 차이가 날 수 있습니다. 두 문법은 다음과 같은 차이가 있습니다.

* `for`: 특정 조건이 성립할 때까지 반복합니다.
  * 인덱스를 하나씩 증가시킵니다.
* `foreach`: 특정 열거(Enumerable) 인터페이스가 열거된 요소를 하나씩 가져옵니다.

`for`문에서 인덱스를 이용해 접근하는 것이 아닌 `enumerator`를 이용하면 더 빨라지겠지만, 결국 이는 `foreach`문을 사용하는 것과 같습니다.

<br>

## 결론

만약  `for`문 대신에 `foreach`를 사용할 수 있는 상황이라면 `foreach`를 사용하는 것이 더 성능에 도움이 될 수 있습니다.

