# #region

* 특정 코드들을 확장, 축소해서 볼 수 있습니다.
* 서로 관련된 필드, 함수, 프로퍼티 등을 그룹지어서 작업할 수 있습니다.

사용 방법은 다음과 같습니다.

> #region *그룹명*
>
> // 그룹 내 코드
>
> #endregion

<br>

### Example

```c#
public class Persion
{
    #region 멤버 필드
    int age;
    string name;
    #endregion
        
   	#region 생성자
    public Persion() {}
    #endregion
        
  	#region 멤버 함수
    public void PrintInfo() {}
    #e
}
```



