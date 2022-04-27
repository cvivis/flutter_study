# flutter_study
플루터 공부하기 



# Flutter

# — 목차 —

# Why? Flutter?

## ㄴ 크로스 플렛폼 프레임워크!

하나의 소스로 안드로이드 ios 배포가 가능하다.

- 신속한 개발이 가능하다. → Hot reloading
- fub.dev를 통한 위젯공유

## ㄴ 단점

- Dart라는 언어사용으로 진입장벽 있음
- 들여쓰기가 깊어져서 가독성이 떨어진다.
- 자료가 부족하지만 왠만하면 다 있다.

# Hot Reloading

`Hot Reloading`
이란 앱의 소스 코드를 수정하면, 앱을 새로 빌드하지 않아도, 즉각적으로 화면에 반영되는 기능을 말한다.

# StatelessWidget vs StatefulWidget

## ㄴ 위젯이란?

> **Everything is a Widget. It’s all Widgets!**
> 

위젯은 UI를 묘사하는 다트의 클래스로 , 화면에 나타날 요소를 결정하는 데이터와 설정. (like 컴포넌트) 

조각난 블럭을 조합하듯이 원하는 앱을 구현함

## ㄴ StatelessWidget

### ㄴ 특징

- 상태가 없기 때문에 상태 관리 X
- 변하지 않는것이 아님, 외부의 정보에 따라 반응한다.
- stl치고 자동완성으로 생성가능

> **constructor(생성자)**
> 

class명과 동일한 이름을 가진 기본 생성자이다. 뒤에 붙은  : super(key : key)는 부모인 StatelessWidget의 기본생성자를 호출한다. 데이터를 전달할 것이 없다면 기본생성자는 생략 가능!

> **bulid**
> 

UI구성하는 함수. 가장 자주 불려지는 함수. 

→ 퍼포먼스 고려할때 유의 

Widget을 리턴하는 함수로 모든 위젯 클래스에 포함되어 있어 블럭 조합하듯 하게 하는 위젯들의 뷰그리게 하는 함수! 

## ㄴ StatefulWidget

### ㄴ 특징

- State 객체를 갖는 위젯
- State 객체의 setState 메서드가 위젯의 상태 변화를 알린다.
- 클라이언트로 인한 state 변화로 setState가 호출되면 플러터가 위젯을 다시그림
- stf 입력후 자동완성가능!
- State 객체 이름 앞에 자동으로 _(언더바) 가 붙어 private를 표현함. 클래스의 경우 같은 파일에서만, property 와 method는 해당 클래서에서만 접근 가능.

```json
class Example extends StatefulWidget {
  const Example({ Key? key }) : super(key: key);

  @override // 상태 생성! 
  _ExampleState createState() => _ExampleState();
}

class _ExampleState extends State<Example> {
  @override
  Widget build(BuildContext context) {
    return Container(...);
  }
}
```

와 같이 **StatefulWidget**을 상속받는 위젯이 **createState**
 메서드로 **State**
 객체를 리턴하고, **State**
를 상속받는 객체가 **build**
 메서드로 **Widget**
을 리턴하는 형태이다.

> **setState**
> 

플러터에게 state값이 변경되었다고 알려서 build 메서드를 다시 호출하게 하는 메서드.

비동기 코드를 실행할 수 없어 setState 실행전 모든 비동기 코드를 완료해야 한다.

- 변경이 필요한 상태값을 **State 객체** 내부에 언더바를 통해 변수를 생성해 준다
- 언더바로 표현한 메소드, 변수와 내부에 **setState**를 이용해 상태 변경 함수를 만든다
- 클라이언트와의 상호작용에 따라 상태 변경이 필요한 곳에 해당 함수를 넣어준다

![Untitled](Flutter%200b6727cf26eb49c795d8175105edd536/Untitled.png)

- initState()는 최초 한번만 실행 - context 접근 X
- didChangeDependencies()최초 한번만 실행 - context 접근 가능
- didUpdateWidet() 해당위젯이 아닌 부모위젯의 변화로 빌드함.
- setState()
- dispose

노랑이들은 특정이벤트 발생시 불러와짐.

