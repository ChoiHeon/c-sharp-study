# unsafe

* `unsafe`키워드는 수행하는 작업이 안전하지 않은 컨텍스트를 나타냅니다.
  * 여기서 '안전하지 않음'이란 CLR에서 안전을 확인할 수 없음을 의미합니다.
  * 안전하지 않은 코드를 사용할 경우, 컴파일 단계에서 에러가 발생할 수 있습니다.
* 안전하지 않은 코드란 포인터를 사용하거나 메모리 블록 할당 또는 해제, 함수 포인터의 사용 등이 있습니다.

<br>

### 사용 방법 예시

```c#
unsafe static void FastCopy(byte[] src, byte dst, int count) {
    // Unsafe context
}

unsafe static void FastCopy(byte* ps, byte* pd, int count) {
    // Unsafe context
}

unsafe
{
    // Unsafe context
}
```

