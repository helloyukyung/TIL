React 공식문서로 디테일 잡기 
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