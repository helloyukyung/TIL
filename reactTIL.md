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

문서를 논리 트리로 표현, 논리적 모델  
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
- babel은 <b>jsx언어</b>를 compile 하여 React.createElement("h1",---) 로 변환 시켜줌 

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

jsx는 변수, 변수안에 html tag를 담을 수 있으며, 그 외의 값들도 변수화 할 수 있음 <br>

props객체로 넣어줬을때 '...props'는  각 요소를 분해해서 보여주는 것을 의미 (js 문법을 jsx에 쓸 수 있음 )

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

