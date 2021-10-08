# dynamic

* 컴파일시 Type Checking을 하는 Static Language, 런타임에 할 경우 Dynamic Language라고 함
* C#은 Static Language이며 Python, Javascript는 Dynamic Language에 속함
* 하지만 C# 4.0부터는 `dynamic` 키워드를 통해서 컴파일시 타입을 알지 못하게 할 수 있음
* 즉, `dynamic` 키워드를 통해서 변수를 선언하면 런타임 도중에 서로 다른 타입의 데이터를 할당할 수 있습니다.



### ExpandoObject

* 사용자가 `dynamic` 타입의 객체를 쉽게 생성하도록 도와주는 클래스

* 즉석으로 속성을 부여하거나 이벤트, 메서드를 할당할 수 있습니다.

  ```c#
  class MyClass {
      public void M1() {
          dynamic person = new ExpandoObject();
          
          // 속성 부여
          person.Name = "Choi";
          person.Age = 27;
          
          // 메서드 할당
          person.Display = (Action)(() =>{
              Console.WriteLine("{0} {1}", person.Name, person.Age);
          });
          person.ChangeAge = (Action<int>)((age) => {
          	person.Age = age;
              if (person.AgeChanged != null)
              {
                  person.AgeChanged(this, EventArgs.Empty);
              }
          });
          
          // 이벤트 초기화
          person.AgeChanged = null; //dynamic 이벤트는 먼저 null 초기화함
  
          // 이벤트핸들러 지정
          person.AgeChanged += new EventHandler(OnAgeChanged);
  
          // 타 메서드에 파라미터로 전달
          M2(person);
      }
      
      // 이벤트 핸들러
      private void OnAgeChanged(object sender, EventArgs e)
      {
          Console.WriteLine("Age changed");
      }
  
      // dynamic 파라미터 전달받음
      public void M2(dynamic d)
      {
          // dynamic 타입 메서드 호출 
          d.Display();
          d.ChangeAge(20);
          d.Display();
      }
  }
  ```

* `IDictionary`로 캐스팅해 내부를 확인 가능

  ```c#
  void M1() {
      // 위와 동일
      
      // ExpandoObject를 IDictionary로 변환
      var dict = (IDictionary<string, object>)person;
  
      // person 의 속성,메서드,이벤트는
      // IDictionary 해시테이블에 저정되어 있는데
      // 아래는 이를 출력함
      foreach (var d in dict)
      {
          Console.WriteLine("{0}: {1}", d.Key, d.Value);
      }
  }
  ```

  ```
  // output
  Name: Choi
  Age: 27
  Display: Action
  ...
  ```

  



