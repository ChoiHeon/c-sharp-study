# fixed

* `unsafe` 구문에서 사용 가능
* 블럭 안에 있는 변수를 GC의 대상이 되지 않도록 함
* 주로 포인터를 사용해야 할 때 사용하는 키워드인 듯

<br>

### Example

```c#
unsafe public static void Foo() {
    Point p = new Point();
    
    fixed (int* x = &p.x) {
        *x = 1;
    }
}
```



