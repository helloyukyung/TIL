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
 표현, 논리
문서를 논리 트리로적 모델  
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
  즉, 돔에 접근해서 돔을 바꾸는게 아니라 가상 돔을 바꿈 