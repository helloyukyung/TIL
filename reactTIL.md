# React

 라이브러리 vs 프레임워크 
 -------

- 라이브러리는 개발 편의를 위한 도구의 모음 (자유도가 높음)(공구)   

- 프레임워크는 기반 구조까지 잡혀있는 것 (공장)

 트렌드 
 -----

 - 기술의 트렌드는 빨리 변함. 
 - 프론트엔드가 각광받기 시작한지 그리 오래되지 않았다. 

 - 새로운 기술을 빠르게 익히는 것이 중요 


DOM 
----
Document Object Model 

문서를 트리로 표현(논리트리), 논리적 모델  
- W3Sschools /createElement
- element(우리눈에 보여지는 것 )
- dom (컴퓨터, 브라우저가 이해하는 elements의 원형, 메모리에 웹 페이지 문서구조를 표현함으로써 스크립트 및 프로그래밍 언어와 페이지를 연결)
- codesandbox : 프론트엔드 코드를 작성하고 이것저것 시도해볼 수 있는 모래상자


CDN
----
Content Delivery Network 
웹에서 사용되는 다양한 컨텐츠(리소스)를 저장하여 제공하는 시스템 
static file(html(정적))안에서 react 를 사용할 수 있음, unpkg

React/ React-dom
----

```java
const rootElement = document.getElementById("root");
const element = React.createElement("h1", {className:"title",
                     children: "hello world" });
ReactDOM.render(element, rootElement);// 주입할 element와 container(rootelement) 입력 
console.log(element);


```

- react는 element를 생성 하는데 쓰였고, 
react dom은 appendchild와 같은 render를하는 역할  

- react가 새로운 객체를 만들어 냄, 그 안에 props가 있고 그 안에 children(hello world)이 존재 (props는 null 로 대체 가능)

------

* createElement:
```java
const element = React.createElement("h1", {className:"title",children: "hello world" },
                    " hello world!!!!");
```
+ 만약 {}인자가 위와 같이 3개가 존재할 때는 마지막 인자인 hello world!!!!가 출력됨 (props로 children을 줬어도)
+ children은 여러개 입력 가능 
+ 실제 react에서는 createElement를 사용하기 보다 "jsx"를 사용 



JSX 
----

문자도 HTML도 아닌 Java Script의 확장 문법, 
HTML과 Javascript 사이를 왔다갔다(?) 할 수 있음 굳 

```
const element =<h1>Hello, world<h1>;
```

- React에서 JSX를 쓰기위해서는 Babel 이 필요( Babel : javascript compiler)
- compiler(컴파일러) : 언어 해석기, 특정 언어를 다른 프로그래밍 언어로 옮기는 프로그래밍 
- babel은 <b>jsx언어</b>를 compile 하여 React.createElement로 변환 시켜줌 //babel unpkg cdn

``` jsx
const rootElement = document.getElementById("root");
const text = "Hello, world !"
const titleclassName ="title 123"
const customH1 = <h1 className={titleClassName} >{text}</h1>
const element = customH1;
ReactDOM.render(element,rootElement);
```

Spread연산자 
----

 props객체로 넣어줬을때 '...props'는  각 요소를 분해해서 보여주는 것을 의미 (js 문법을 jsx에 쓸 수 있음 )
- jsx는 변수, 변수안에 html tag를 담을 수 있으며, 그 외의 값들도 변수화 할 수 있음 <br>

```jsx
const rootElement = document.getElementById("root");
const text = "Hello, world !"
const titleclassName ="title 123"
//const props = {className :titleClassName, children: text} ==
//const customH1 = <h1 className ={props.className} children ={props.children}/ > ==
const customH1 = <h1 {...props}/>
const element = customH1;
ReactDOM.render(element,rootElement);
```

멀티 element생성 (Fragment)
----

주입된 root element는 1개이지만 안에 여러가지 element(h1,h2,h3)를 넣어줌 

```jsx
const rootElement = document.getElementById("root");
const element = (
    <div className="box" children ={ //==<React.Fragment children={}... >
    [   
        <h1>hi</h1>//jsx
        React.createElement("h2",null, "bye")}>
        React.createElement("h3",null, "hello")}>

    ] 
    );
ReactDOM.render(element,rootElement);
```
- React.Fragment를 쓰면 요소들을 div 안에 넣지 않고도(box) root 안에 표현 가능 <br>
  React.Fragment는 부모로써 감싸주는 역할만 (실제 html을 작성할 때는 노출되지 않음)

<br>
- 깔끔하게, 빈 <></>는 React.Fragment를 의미함 

```jsx
const element = (
    <>
                <h1>hi</h1>
                <h2>bye</h3>
                </>
                );
```

Element 찍어내기 ,재사용 가능한 element
----
```jsx
  const Paint = ({title, description}) => {
      return (
        <>
        <h1>{title}</h1>
        <h2>{description}</h2>
        {children}
        </>
      );
  };


      const element = (
        <>
        <Paint title="Good" description="good"/> 
         {Paint ({title:"Bad", description:"bad", children :"hi" ,children :"hi"})}
        </Paint>
        // {paint("Hello","hello")}
        </>
      );
```
- React.creatElement; Paint -> props, element ->element 
- 위에서 title="Good",  description="good", children= {Paint ({title:"Bad", description:"bad", children :"hi" ,children :"hi"})}

js 와 jsx 섞어 쓰기1(If else)
----
```jsx
      const Text = ({ text }) => {
        //text가 대문자로 시작하면 h1, 소문자로 시작하면 h3
        if (text.charAt(0) === text.charAt(0).toUpperCase()) {
          return (
              <h1> {/*jsx*/}
              {text} {/*js*/}
              </h1> //jsx
              );
        } else {
          return <h3>{text}</h3>;
        }
      };
      const element = (
        <>
          <Text text="Text" />
          <Text text="text" />
        </>
      );
```

- 같은 custom component를 썼지만 결과물은 다르도록 출력= Interpolation

js 와 jsx 섞어 쓰기2(삼항 조건 연산자) 
----
```jsx
      function Number({ number, selected}) {
        return number % 2 === 0 ? <h1>{number}</h1> : <h3>{number}</h3>;
      }

      const element = (
        <>
          <Number number={1} />
          <Number number={2} selected ={true} />
          <Number number={3} />
        </>
      );
```
- 조건 ? true : false 


js 와 jsx 섞어 쓰기3(map)
----
```jsx
      function Number({ number, selected }) {
        return selected ? <h1>{number}</h1> : <h3>{number}</h3>;
      }

      const element = (
        <>
          {[1, 2, 3, 4, 5, 6, 7, 8, 9, 10].map((number) => (
            <Number className="title" key={number} number={number} selected={number === 3} />
          ))}
        </>
      );

```

프론트엔드 개발의 장점 
----

눈에 보이므로 눈으로 바로 확인하기 
- google/MDN/console 참고하기 

-----------------
리액트와 리렌더링 
====

바닐라 js -> 변경으로 인해 element를 다시 그림 
React -> 변경된 부분만 다시 그림 

In 바닐라 js(1)
----
```js
const rootElement = document.getElementById("root");
const number = Math.floor(Math.random() * (10 - 1) + 1); // 10보다 작고 1보다 큰 random 값을 만듬 
const element = `<button>${number}</button>`;
rootElement.innerHTML = element;
```

-  Math.random() * (max - min) + min : 두 값 사이의 난수 생성, 함수의 반환값은 Min 보다 크거나 같고, Max보다 작음 
-  Math.floor : 뒷자리 올림

In 바닐라 js(2)
----
```js
const rootElement = document.getElementById("root");
function random() {
  const number = Math.floor(Math.random() * (10 - 1) + 1); // 10보다 작고 1보다 큰 random 값을 만듬
  const element = `<button>${number}</button>`;
  rootElement.innerHTML = element;
}
setInterval(random, 1000);

```
- setInterval: 특정 함수를 특정 시간동안 반복 

In React(1)
----
```jsx
<script type="text/babel">
  const rootElement = document.getElementById("root");
function random() {
  const number = Math.floor(Math.random() * (10 - 1) + 1); // 10보다 작고 1보다 큰 random 값을 만듬
  const element = (
  <>
   <button>{number}</button>;
   <button children={number}/>
   <div><p>{number}</p><div>;
  
  </>
  )

  ReactDOM.render(element, rootElement);
}
setInterval(random, 1000);
</script>
```
* vanila js와 react 의 차이 
 + vanila의 경우 tab을 눌렀을 때 계속 풀림 -> div의 root, button이 바뀜 (변경으로 인해 element를 다시 그림)
 + react의 경우 tab이 풀리지 않고 있음 -> button 안의 숫자 (바꾸려고 하는)값만 바뀜 (변경된 부분만 다시 그림)
+ 효율적으로 바꾸고자 하는 곳만 바꿀 수 있음 , 부모 (위 div 에는 영향을 미치지 않음)


리엑트 문서 
----
React 앨리먼트는 불변객체(immutable)(변하지 않는 객체)이다. <br>
우리는 그저 ReactDOM.render(element, rootElement);로 전달할뿐, <b>변경판단 및 반영</b>은 리액트가 알아서 한다.

- DOM element type이 같은 경우(위 코드와 같이): 동일한 내역은 유지하고 변경된 속성(props,{number}) 들만 갱신함 
- element 타입이 바뀌면 이전 앨리먼트는 버리고 새로 그리며, 앨리먼트 타입이 같다면 (key를 먼저 비교하고,key가 같다면) props를 비교해서 변경사항을 반영한다. 
- tree를 이야기할 때, dom은 화면에 그려지고 보여지는 애가 아니라 논리적으로 브라우저가 인지하고 있는 tree 개념 , 그것을 그린게 element임(실제 눈에 보여지는 애)-> react는 dom 을 어떻게 비교할까?
- virtual dom: 이전virtual dom과 새로 들어온virtual dom을 비교, 재조정 알고리즘(Reconciliation)을 통해 업데이트 함
  즉, 돔에 접근해서 돔을 바꾸는게 아니라 가상 돔(필요한 부분만) 바꾸는 것 
<br>
<br>
-------------
<br>
eventHandler이벤트 핸들러
----

event : 사용자의 동작, 브라우저의 변경을 코드가 인지 


Vanila JS에서 event를 적용하는 방법  
---- 
 addEventListener, on{event}, onclick="", onmouseout, onfocus, onblur...등

```js
<button onclick="document.getElementById('demo').innerHTML=Date()">The time is?</button> 
<p id="demo"></p>
```
- inline 방식( tag안에 넣음 )

```js
<script>
	const button = document.getElementById("button");
    button.addEventListener("mouseout",()=> alert('bye'));
</script>
```
- addEventListener를 통해 직접 입력하는 방식

React에서 event를 적용하는 방법 
----
on{Event}, onClick, onMouseOut onFocus,onBlur

리엑트는 <b>카멜 케이스</b>로 표현<br>
- 기본 문장 : on click 
- 카멜 케이스 : onClick
- 파스칼 케이스 : OnClick
- 케밥 케이스 : on-click
- 스네이크 케이스 : on_click

```jsx
const rootElement = document.getElementById("root");
const handleClick = () => {
  alert("pressed");
};
const element = (
  <button onClick={handleClick} onMouseOut={() => alert("bye")}>
    press
  </button>
);
ReactDOM.render(element, rootElement);
```


- React 또한 inline, 함수로도 표현 가능 
- addeventlistener 도 사용 가능하나 보편적으로(또 편하니까) inline 안에 함수를 집어넣어 표현함 


event handler 써보기 
----

``` jsx
     const rootElement = document.getElementById("root");

      const state = { keyword: "", typing: false, result: "" }; // 전역변수

      const App = () => {
        function handleChange(event) {
          setState({ typing: true, keyword: event.target.value }); // inline에 넣어준 함수가 알아서 event객체를 가져와줌

          function handleClick() {
            setState({
              typing: false,
              result: `We find results of ${state.keyword}`
            });
          }

        return (
          <>
            <input onChange={handleChange} />
            <button onClick={handleClick}>search</button>
            <p>
              {state.typing ? `looking for...${state.keyword}` : state.result}
            </p>
          </>
        );
      };

      function setState(newState) {
        Object.assign(state, newState); 

        render(); // setState를 할때마다 rander를 다시 돌려줌
      }

      function render() {
        ReactDOM.render(<App />, rootElement);// reaact가 알아서 dom 안에서 변경이 없으면 변경이 있는 props들만 바꿔줌 

      }
      render();
    </script>
```

- Object.assign : 객체 내용 복사, 이전 객체(출처객체)를 새로운 객체(대상 객체)로 덮어 씀 다른 부분이 있으면 덮어쓰고 같으면 유지 
- 전역 변수 변경 ReactDOM.render 에서 render함수를 새로 부르면서 업데이트 시킴

-------
<br>

컴포넌트 상태다루기- useState
----
- 컴포넌트란?<br>
 DOM: 논리트리<br>
 컴포넌트 : 앨리먼트(element)의 집합 <br>
 앨리먼트 : 컴포넌트의 "구성요소" <br>

- 위 코드에서 App-> component임 input, button 등 element들의 집합체이므로 
```jsx
<div id="root"></div>
<script type="text/babel">
  const rootElement = document.getElementById("root");

  const App = () => {
    const [keyword, setKeyword] = React.useState(""); // useState: render를 다시 해주지 않아도 적용이 됨
    const [result, setResult] = React.useState("");
    const [typing, setTyping] = React.useState(false);

    function handleChange(event) {
      setKeyword(event.target.value);
      setTyping(true);
    }

    function handleClick() {
      setTyping(false);
      setResult(`we find results of ${keyword}`);
    }

    return (
      <>
        <input onChange={handleChange} />
        <button onClick={handleClick}>search</button>
        <p>{typing ? `looking for ${keyword}...` : result}</p>
      </>
    );
  };

  ReactDOM.render(<App />, rootElement);
</script>
```
- useState : 컴포넌트 안의 상태값을 관리해주는 훅
<br>


컴포넌트 사이드 이펙트 다루기 - useEffect
----

사이드 이펙트 = 부작용 

의도하지 않은 효과  vs 부수 효과 <br>
변경 효과가 일어날때, 다른곳으로 부수적인 효과를 줌.
keyword값이 바뀌었을때 부수적으로 local storage에 저장 

```jsx
const App = () => {
  const [keyword, setKeyword] = React.useState(
    ()=>{ window.localStorage.getItem("keyword")}// window의 localstorge에 도달해서 꺼내와야하기때문에 딜레이가 발생함
  );
  const [result, setResult] = React.useState("");
  const [typing, setTyping] = React.useState(false);

  window.localStorage.setItem("keyword", keyword);// 바뀔때마다 계속 local Storage를 굴림 나는 "keyword"가 바뀔때마다 저장하고 싶음

  function handleChange(event) {
    // window.localStorage.setItem("keyword", event.target.value); 
    setKeyword(event.target.value);
    setTyping(true);
  }
```
- App component에 console.log("render")를 해보면 값이 바뀔때마다 "render"가 뜨는 것을 볼 수 있음 
- 계속 window의 localstorge에 도달해서 꺼내와야하기때문에 딜레이가 발생함
- getItem은 window의 localstorge에 도달해서 꺼내와야하기때문에 시간이 발생하므로 <b>함수</b>로 값을 넣어줌 (초기값을 return하는 함수-> <b>함수</b>를 사용하면 initializing 하는 것을  delay, lazy하게 줄 수 있음, 바로 값을 못가져오면 버퍼가 생길 수 있으므로)

```jsx 
React.useEffect(()=>{
  console.log("effect");// render되는 모습 확인 
  window.localStorage.setItem("keyword",keyword);
},[ keyword , typing] );
```
- useEffect : 첫번째 인자는 함수(실행), 두번재 인자는 배열(dependency array의존성 ),(사이드 이펙트를 일으키고 싶은 대상을 넣어줌. 안넣어도(모든 변화에 반응) , 빈배열을 넣어도 됨(처음에만 동작)) 
- keyword, typing이 바뀔때마다 이를 React가 인지하고 함수를 실행하게 함 


커스텀 훅(custom Hook) 만들기 
----
짝어내기 / 반복 => 함수화 <br>
useState/useEffect를 반복 => 커스텀 훅<br>
- useLocalStorage

```jsx
function useLocalStorage(itemName, value="") { // default value는 브라우저에서 이미 갖고있는 값 
  // item name을 넘겨주도록 함
  const [state, setState] = React.useState(() => {
    window.localStorage.getItem(itemName) || value;// 두번째 인자를 안넣어 줬을 때는 "" 빈 값 
  });
  React.useEffect(() => {
    window.localStorage.setItem(itemName, state);
  }, [state]);
  return [state, setState];
}
//--- in app component
const App = () => {
  const [keyword, setKeyword] = useLocalStorage("keyword");
  const [result, setResult] = React.useState("");
  const [typing, setTyping] = React.useState("typing", false);//boolean의 경우
```
-  커스텀 훅(useLocalStorage)을 만듦으로 코드를 좀 더 효율적으로 사용할 수 있음


hook flow 이해하기 (App- child)
----
<a href="https://github.com/yukyung123/TIL/blob/master/code/hookflow(1).html">참고 code</a> 

hook flow -> hook 들의 호출 타이밍 <br>
useSatate -> setState 시 prev이 주입된다. 



- console.log 순서  
1. APP render start 
2. App useState
3. APP render End
4. (1)useEffect, no deps # 모든 변화에 
5. (2)useEffect, empty deps #처음에 render 될때만
6. (3)useEffect, [show] # []값이 바뀔때만

  + useEffect는 deps에 따라 다르게 호출될 수 있음 
  + APP render가 끝난 뒤에 useEffect가 동작함-> sideeffect



hook flow 이해하기2 (App- child)
----
<a href="https://github.com/yukyung123/TIL/blob/master/code/hookflow(2).html">참고 code</a>


- search 버튼을 눌렀을 때(show가 눌림 )
1. APP render start 
2. APP render End
3. child render start  
4. Child useState 
5. child render end  
6. child useEffect, no deps <br>
   child useEffect, empty deps<br>
   child useEffect, [text] 
7. App useEffect, no deps<br>
   App useEffect, [show] 


child가 다 그려지고 children use effect가 일어난 뒤 그다음 app의 useeffect가 일어남

- input에 글자를 입력할때
1. child render start  
2. child render end
3. child useEffect, no deps <br>
   child useEffect, empty deps<br>
   child useEffect, [text] 

- search 버튼을 눌러 껐을 때 (false)

1. APP render start 
2. APP render End
3. App useEffect, no deps
4. App useEffect, [show] 

clean up
----
- setup해 놓은 sideEffect를 다시 동작할 때 기존에 세팅되어있는것을 다 지움 
- 처음생성할때 clean up은 안불림 
- 한번이라도 useeffect가 등록이 되어 있었으면 cleanup -> use effect
- 부모의 cleanup이 먼저 일어나고 children cleanup
- children render-> app clean up -> child use effect -> app use effect
- 불변객체를 만들어줌 

정리 
----
- useEffect -> render가 끝난뒤 실행된다 
- update시 -> useEffect clean up / useEffect 
- dependency array -> 전달받은 값의 변화 있는 경우만 


리액트 element에 스타일 입히기 (style)
----
리액트의 장점 : html과 js 를 섞어쓰는 jsx, 함수로 빼낼 수 ㅇ

```jsx
  function Button({ props }) {
    console.log(JSON.stringify(props));//객체를 글자로 바꿔서 보여줌 = undifined
    return <button className="button" {...props}></button>;
  }
      const element = (
    <>
      <Button className="button" style={{ borderRadius: "50%" }}>
        Green
      </Button>
      <Button className="button blue" style={{ borderRadius: 8 }}>
        Blue
      </Button>
      <button className="button red">Red</button>// html
      <button className="button gray">Gray</button>// html
      <button className="button black">Black</button>//html
    </>
  );
```
- 그냥 button만 출력되고 css는 꾸며지지 않음 ->우리는 element에서  props'객체'를 받지 않았음  
- props 자체는 모든 객체를 나타냄 즉, function Button( props ) 이렇게 표현해야 정상적으로 작동  


- props = {className, style, children...}   
- props = {className, style, ...rest}
- className -> 문자열 
- style -> 객체 카멜케이스, className보다 먼저 


----
Ref로 Dom 다루기 (useRef)
----
<a href="https://github.com/yukyung123/TIL/blob/master/code/Ref_DOM.html">참고 code</a>

Ref: reference준말 

useRef: DOM을 다루는 hook, 값을 특정할 수 있음  

- Input Element가 있고 화면이 뜨자마자 focus를 주고 싶다면?<br>
  ->in js -> ?.focus();

- <del>왜 이걸 DOM 조작하기라고 할까 element조작하기 아닌가,,,</del>

- document.getElementById류를 사용하지 않고 useRef를 사용할까->
document에 접근하여 이용하면 비효율 발생할 수 있음 (react가 관장하게 끔 하자)
- 전역적으로 관리하거나, component상태안에서 독립적으로 react에 최적화된 (저장공간) 기능을 쓰고 싶을 때 useRef사용 

Form다루기 1
----

  onSubmit->  event.preventDefault() ; 이벤트의 기본 동작을 막음  
  event.target.elements -> console.dir(element) ; 
  특정 event target을 console.log 함으로써 element, input의 값을 알 수 있었음 
 

Form다루기 2 (uncontrolled ve controlled)
----
<a href="https://github.com/yukyung123/TIL/blob/master/code/form.html">참고 code</a>
- validation 체크 ; input으로 입력되는 값에 따라서 onsubmit에서 validation check or 입력하자마자 보고싶어서 handlechange 에다가 그 값이 0 인지에 따라 값을 보여줌
- 
- value: react에서 set해주는 값을 직접 바꾸고 싶을 때, value를 input tag에 넣어주고 state를 직접 넣어줌. (disabled도,,, )

```jsx
disabled={
!phoneNumber.length === 0 || message !== "Phone Number is vaild"
}
```
- 메세지 값이 하나라도 있었으면 좋겠음 //  메세지가 "Phone Number is vaild" 할때 제출되길 원함 
- error : phone number가 0 이어도 Phone Number should starts with 0 됨 
- 이유 : handlechange()에서 setPhoneNumber()값이 싱크가 맞지 않아서,,,<br>
        usestate , setPhoneNumber에서 바로 값을 가져다 쓰니까 에러가 났음 <br>
        그래서 이벤트로 온 값을 쓰고 , state를 업데이트 해줘야할 때, setPhoneNumber를 뒤에 붙여줌 

- validation -> onChange에서 하는게 편함 
- controlled -> input의 value를 직접 react componemt에서 관리 

------

Error다루기 (catch error)
----
<a href="https://github.com/yukyung123/TIL/blob/master/code/catch_error.html">참고 code</a>
- in js

```js
try{
  //... error가 날 수 있는 위험한 code 
} catch (error){
  // error 가 났을 때, 어떻게 처리할 수 있는지 
}
```
- Error Boundary -> catch Error해서 보여주기 

- FallBack -> Error 가 났을때 보여줄 컴포넌트 

- 어떨 때는 자바스크립트의 error때문에 react의 component가 안그려질 수도 있음 
- ErrorBoundary: React에서 <child/>에서 error가 났어도,, 정상적으로 작동하는 다른 부분은 보여주게 만들고 싶을때, 
- 함수형 component가 아닌 class, error가 났을 때 상태값을 처리하는 getDerivedStateFromerror 함수를 class에서만 제공하기 때문에 
<br>

---------

Ket와 리랜더링 알아보기 (What is Key)
----
<a href="#">참고 code</a>
Key-value 
-DB, Dictionary, Json, Object ...
- Key는 value 를 특정하는 이름 


Key와 리랜더링 알아보기 (Detail 이전 코드 확장)
----
<a href="https://github.com/yukyung123/TIL/blob/master/code/key_value(1).html">참고 code</a>

- key를 안줬을 때는 버튼은 그대로 있는데, 값들만 바꿔치기됨( key={index} )

- 재조정 알고리즘에서도, 자식들이 key를 가지고 있다면, React는 key를 통해 기존트리와 이후 트리의 자식들이 일치하는지 확인 

- 재사용 -> key값을 제대로 줘야 재사용 가능 ex) 재배열 할때 index를 키값으로 준다면,,, X
- 제대로 준다 -> 중복없고, 바뀌지 않는 


----


상태끌어올리기 (State lifting up)
----
<a href="https://github.com/yukyung123/TIL/blob/master/code/state_lifting%20up.html">참고 code</a>

- 형제의 상태를 알 방법이 없음 -> 부모로 상태의 관리를 끌어올림 
- 다시, 형제 컴포넌트의 상태 궁금 -> 필요하면 부모(서로의 공통된)로 lifting up
- Props drilling -> 과도한 lifting은 drilling 을 야기,,

<br/>

-----

데이터 Fetch해보기(API call)
----
Fetch란 네트워크 통신
화면을 그릴때 서버가 데이터를 줄거고 프론트는 그 데이터를 가지고 화면에 나타나게 해줌
- React에서 데이터를 가져와보기

Fetch API: 네트워크 통신을 포함한 리소스 취득을 위한 인터페이스가 정의되어 있음
https://developer.mozilla.org/ko/docs/Web/API/Fetch_API#%EA%B8%B0%EB%B3%B8_%EA%B0%9C%EB%85%90%EA%B3%BC_%EC%82%AC%EC%9A%A9_%EB%B0%A9%EB%B2%95

JSON : 데이터를 표현하는 데이터 포멧의 일환 

<a href="https://github.com/yukyung123/TIL/blob/master/code/data_fetch.html">참고 code</a>

```jsx
{JSON.stringify(data, null, 2)}
```

- json형태를 우리가 원하는 형태로 만들어줌

<br/>
정리 

- Fetch api -> 네트워크 통신 도구 
- 상황별 핸들링 -> 로딩 (loading...)/ 데이터 / 에러 (.catch)