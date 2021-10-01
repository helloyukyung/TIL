React 공식문서로 디테일 잡기 (초급)
====

공식문서를 보는 이유와 방법 
----
라이브러리는 만든 사람이 있다. <br/>
그들이 만든 목적과 도구의 사용법을 정리해뒀다. (사용 설명서)<br/>
리액트의 공식문서는 친절하고, 한국어 번역도 거의 있고,Tutorial 도 있음 


공식문서를 보는 방법은 목적에 따라 나뉨

바로 <b>써보기</b> vs <b>이해해보기</b>

모든것은 연습/반복 

환경설정 (vscode)
----
- Visual Studio Code (aka. vscode) : Javascript로 만들어진 IDE(통합개발 환경)

- Visual Studio Code Extensions : IDE를 풍성하게 해주는 여러 기능들이 있음 

- Node 설치 : 로컬 (컴퓨터) 에서 리액트 앱이 돌아갈 수 있도록 해주는 환경 

- tmi) Node를 깔면, npm(node package manager)도 자동으로 설치됨, npm이 설치되면 npx(node package runner)도 자동으로 설치됨


공식문서로 보는 JSX 
----

- JSX속성

 속성에 따옴표를 이용해 문자열 리터럴을 정의할 수 있다.<br/>

JSX는 HTML보다는 JavaScript에 가깝기 때문에, React DOM은 HTML 어트리뷰트 이름 대신
camelCase 프로퍼티 명명규칙을 사용한다.(tabindex-> tabIndex)

```jsx 
const element <div tabIndex="0"><div>;
```
중괄호를 사용하여 어트리뷰트에 JavaScript 표현식을 삽입할 수도 있다.

```jsx
const element <img src={user.avatarUr}></img>
```

- JSX는 객체를 표현

 Babel은 JSX를 React.createElement() 호출로 컴파일 한다. 
 (다음 두 예시는 동일함)

 ```jsx
 const element =(
     <h1 className ="greeting">
    dddddd Hello world
     </h1>
 )
```

```jsx
const element =React.createElement(
    'h1',
    {className:'greeting'},
    'helloworld'
);
```


------

Props(공식문서로 보는 Props)/(Component and Props)
----
컴포넌트는 JavaScript함수와 유사 'props'라고 하는 임의의 입력을 받은 후 , <br/>
화면에 어떻게 표시되는지를 기술하는 React element를 반환 

함수 컴포넌트와 클래스 컴포넌트 
----
컴포넌트를 정의하는 가장 간단한 방법은 Javascript함수를 작성하는 것 
```jsx
function Welcome(props) {
    return <h1>hello,{props.name} </h1>
}
```
이 함수는 데이터를 가진 하나의 'props' (props는 속성을 나타내는 데이터) 객체 인자를 받은 후 
React 엘리먼트를 반환하므로 유효한 React컴포넌트 이다. <br>
이러한 컴포넌트는 JavaScript함수이기 때문에 말 그대로 '함수 컴포넌트'라고 호칭 한다. <br>
또한 ES6를 사용하여 컴포넌트를 정의할 수도 있다. 
```jsx
class Welcome extends React.Component {
    render()
    return <h1>Hello, {this.props.name}</h1>;
}

```
React의 관점에서 볼 때 위 두가지 유형의 컴포넌트는 동일 


컴포넌트 렌더링 

이전까지는 React 엘리먼트를 DOM태그로 나타냈다.

```jsx
const element = <div>
```
React엘리먼트는 사용자 정의 컴포넌트로도 나타낼 수 있다

```jsx
const element = <Welcome name="sara">
```

React가 사용자 정의 컴포넌트로 작성한 엘리먼트를 발견하면 
JSX 어트리뷰트와 자식을 해당 컴포넌트에 단일 객체로 전달한다. 그리고 이 객체를 'props'라고 한다.

다음은 페이지에 'hello, sara'를 렌더링 하는 예시 

```jsx
function Welcome(props) {
    return <h1>Hello, {props.name} </h1>
}
const element = <Welcome name= "sara"/>
ReactDOM.render(
    element, document.getElementById('root')
)

```
위 예시에서는 
1. ```<Welcome name= "sara"/>``` 엘리먼트로 ReactDOM.render() 를 호출 
2. React는 {name:'Sara'}를 props로 하여(전달받아) Welcome 컴포넌트를 호출 
3. Welcome 컴포넌트는 결과적으로 ``` <h1>Hello, {props.name} </h1>```를 반환 
4. React DOM은 ```<h1>Hello, {props.name} </h1>```엘리먼트와 일치하도록 DOM을 효율적으로 업데이트 

(주의 : 컴포넌트의 이름은 항상 대문자로 시작 )

컴포넌트 합성 
----
컴포넌트는 자신의 출력에 다른 컴포넌트를 참조할 수 있다. 
이는 모든 세부단계에서 동일한 추상 컴포넌트를 사용할 수 있음을 의미한다. 
React앱에서는 버튼, 폼, 다이얼로그. 화면 등의 모든 것들이 흔히 컴포넌트로 표현된다. 

예를들어 Welcome을 여러번 렌더링 하는App 컴포넌트를 만들 수 있다. 

```jsx

function Welcome (props) {
    return (<h1>Hello, {props.name} </h1>)

}

funcion element () {
    return(
        <>
        <Welcome name = "jenny"/>
        <Welcome name = "jisu"/>
        <Welcome name = "lisa"/>
        <Welcome name ="rose"/>
        </>
    )
}
ReactDOM.render( element, document.getelementById("root") )


```
React extension - rfc ; react functional component를 자동생성해줌 


Prop(정리)
----
Props -> 컴포넌트에 전달되는 단일 객체 
순수함수처럼 동작 -> Props 자체를 수정해서는 안됨 
컴포넌트 합성 -> 여러 컴포넌트를 모아서 
컴포넌트 추출 -> 여러곳에서 사용되거나/ 복잡한 경우 

-------


State and Lifecycle 
----
function component에서는 return 한 값이 곧 render() 였다. <br/>
하지만 class component 에서는 render()가 따로 존재, 그곳에서 리턴 값을 그려준다. 
class component 와 똑같은 function component를 만들어볼 것이다. 

  classs componet 코드 :<br/>
  function component 코드 :

State(정리) 
----
컴포넌트 내의 상태 -> 자신의 출력값을 변경(props는 x) 

Class component -> State Life Cycle (state 관리 )

Functional component -> 훅으로 관리 

유의사항 -> 직접수정 X(date= ? X) / 비동기적일 수 있음 <br>
예를들어 ```this.state.comment='hello``` 이 코드는 컴포넌트를 다시 렌더링 하지 않는다. <br>
대신 setState를 사용해주자 ```this.setState({comment:'hello'})```


State 업데이트는 비동기적일 수 있음 

React는 성능을 위해 여러 setState() 호출을 단일 업데이트로 한번에 처리할 수 있다. <br/>
this.props와 this.state가 비동기적으로 업데이트 될 수 있기 때문에 다음 state를 계산할 때 해당 값에 의존해서는 안된다. <br/>
예를들어 다음코드는 카운터 업데이트에 실패할 수 있다. <br/>

```jsx
//Wrong
this.setState({
    counter : this.state.counter +this.props.increment,
})
```
이를 수정하기 위해 객체 보다는 함수로 인자를 사용하는 다른 형태의 setState()를 사용한다.<br/>
 그 함수는 이전 state를 첫번째 인자로 받아들일 것이고, 업데이트가 적용된 시점의 props를 두 번째 인자로 받아들일 것이다. 

 ```jsx
 this.setState((state, props)=>({
     counter: state.counter +props.increment
 }));
 ```

-------
컴퍼넌트 생명주기 
----

React를 사용할 때는 컴포넌트를 class 또는 함수로 정의할 수 있다. 

React 컴포넌트 class를 정의하려면 React.component를 상속 받아야 한다.
 
```jsx
class Welcome extends React.Component {
    render() {
        return <h1> Hello, {this.props.name}</h1>
    }
}
```

render()는 React.component의 하위 class에서 반드시 정의해야 하는 메서드이다. 


arrow function 은 this 가 누구인지 암 

컴퍼넌트 생명주기 (정리)

constructor -> state 초기화 및 메서드 바인딩 

componentDidmount -> Dom 노드 및 데이터 fetch 

componentWillMount -> 타이머 제거 및 요청 취소 및 구독 해제 

Functional Component -> hook 으로 대부분 구현 가능 




----

합성이벤트 (Synthetic Event)
----

인터페이스는 같지만 직접 대응되지 않음 (Html에서 제공한 native event와는 대응되지 않음 )

react는 react를 사용하는 사용자들에게 
일괄된 경험으로 개발할 수 있도록 도와준다. 

이벤트 처리하기 
----
React 엘리먼트에서 이벤트를 처리하는 방식은 DOM 엘리먼트에서 이벤트를 처리하는 방식과 매우 유사하다. 
몇가지 문법 차이는 다음과 같음
- React의 이벤트는 소문자대신 캐멀케이스 (camelCase) fmf tkdydgksek. 
- JSX를 사용하여 문자열이 아닌 함수로 이벤트 핸들러를 전달한다. 

HTML에서는
```html
<button onclick =activateLasers()>
    Active Lasers
</button>

```
React에서는 
```jsx
<button onClick ={AcativeLasers}>
    Active Lasers 
</button>
```
- 또한 React에서는 false를 반환해도 기본동작을 방지할 수 없다. 
반드시 preventDefault()를 명시적으로 호출해야 한다.<br>

예를 들어, 일반 HTML에서 폼을 제출할 때 가지고 잇는 기본 동작을 방지하기 위해 다음과 같은 코드를 작성할 수 있다. 

```html
<form onsubmit="console.log('you clicked submit.');
return false">
<button type="submit">Submit</button>
</form>
```
React에서는 다음과 같이 작성 
```jsx
function Form () {
    function handleSubmit(e) {
        e.preventDefault();
        console.log('you clicked submit')
    }

    return (
        <form onSubmit={handleSubmit}>
            <button type="submit">Submit</button>
        <form>
    )
}

```
여기서 e는 합성이벤트 


<br>

이벤트 핸들러에 인자 전달하기 
----
루프 내부에서는 이벤트 핸들러에 추가적인 매개변수를 전달하는 것이 일반적. 
예를들어 id 가 행의 ID일경우 다음 코드가 모두 작동 

```jsx
<button onClick={(e)=> this.deleteRow(id,e)}>
Delete Row
</button> 
<button onClick={this.deleteRow.bind(this,id)}>
Delete Row
</button>
```

지원하는 이벤트
----
React는 이벤트들을 다른 브라우저에서도 같은 속성을 가지도록 표준화 한다. 

capture 를 덧붙이는이벤트 ->이벤트 버블링 단계에서 호출
 
 버블링 : 어떤 element를 클릭했을 때, 이벤트를 그 부모로 계속 전달하는 것 

캡쳐링 : 부모가 자식들에게 누가 클릭이되었는지 체크하는것 

캡쳐링 후에 버블링이 일어남 

이벤트 (정리) 
----
합성이벤트 -> 인터페이스는 같지만 직접 대응되지 않음 

Bubble/Capture -> Capture -> target -> Bubble 

return false -> e.preventDefault() 해줘야 함 

----


조건부 렌더링 (Conditional Rendering)
----
React에서는 원하는 동작을 캡슐화하는 컴퍼넌트를 만들 수 있음.

이렇게 하면 애플리케이션의 상태에 따라서 컴포넌트 중 몇 개만을 렌더링 할 수 있다. 


- if -> if(condition){return A} else {return B}
- && -> condition &&A, falsy 주의 (해결 boolean 강제, or 삼항)
- 삼항연산자 -> condition ? A: B
- 아예 안그리고 싶은 경우 -> return null;


----

List( 리스트와 Key)
----
같은 컴퍼넌트가 여러개 그려져 있는 것 (map과 관련,,)

key값은 element가 특정한지 고유성을 판단할 때만 쓸 뿐, 자식에게 데이터가 넘어가지 않음 (key는 props가 아님 )/ ```props.id```는 읽을 수 있으나, ```props.key```는 읽을 수 없음 

List 정리 
----
- map -> 배열의 개별 요소를 순회(item을 첫번째 인자로, index를 두번째 인자로 받음 ) 
- default key -> 안주면 react는 index를 쓴다(재배열된다면,, Warnning)
- 고유성 -> 형제 사이에서만 고유하면 됨 
- key props -> key는 props로 넘어가지 않음 

----

Form 
----
제어 컴포넌트(controlled Component) : component자체에 value를 주고 value를 state로 관리하고 있는 것.

react가 상태를 직접 관리 

제어 컴포넌트를 구현하는데 value어트리뷰트를 허용 

 uncontrolled submit : 리엑트는 value에 대해 모르고 있음 


 Form (정리)
 ----

 - Controlled Component -> input의 value를 state로 관리 
 - 다중입력 -> event.target.name 
 - Uncontrolled Component -> form element자체의 내부 상태 활용
 - defaultValue, ref -> 기본값 / value확인 







