# react-router-dom

react-router-dom은 SPA(Single Page Application) 앱을 만들 때 표준처럼 사용되고 있는 네이게이션 라이브러리이다.

SPA의 단점이 주소가 바뀌지 않는다는 것인데 React Router를 사용하면, 발생하는 라우팅이 location이나 history와 같은 브라우저 내장 API(history API)와 연동이 된다.

즉, react-router-dom를 사용하면, SPA의 장점을 누리면서도 브라우저상의 라우팅(특정 주소 고정, 뒤로가기(기본 SPA는 뒤로가기 버튼을 누르면 이전 페이지가 아닌 그전에 서핑한 다른 웹사이트로 이동), 새로고침 등)을 이용할 수 있다는 것이다.

## Link component

```jsx
<Link to="/potato"/> <div>감자로 가는길</div></Link>
```

HTML의 `<a>` tag와 유사. `<a>`의 `href `속성 대신 `to` props를 통해 이동할 경로를 지정해준다.<br/>
위 코드(경로)는 ex. localhost:3000/potato 로 이동시켜준다.

## Route component

```jsx
<Route path="/potato" element={<Potato />} />
```

위 코드는 현재 주소창의 경로가 /potato 경우 Potato component를 보여준다.
일반적으로 현재 주소창의 URL 경로에 따라 특정 콘텐츠를 보여주거나 숨기기 위해서 사용된다.

### Route에서 props 전달

```jsx
//(X)
<Route path="/tomato" element={<Potato/>} score={score} />

//(O)
<Route path="/potato">
    <Potato score={score}/>
</Route>
```

위 (X) 코드는 Route component에 props를 전달해 준 것 !

## Routes(Switch)

```jsx
<Routes>
  <Route path="/tomato" element={<Tomato />} />
  <Route path="/potato" element={<Potato />} />
//   <div>안돼!<div>
</Routes>
```

Routes는 오직 Route compoment들로 구성된다(`<div>안돼!<div>`(X)).<br/>
이전에는 Switch로 쓰였지만 v6이후부터는 무조건! Routes로 써야 한다.<br/>
또한, 이전에는 `component` , `render` props를 통해 컴포넌트를 전달해 줬다면 v6 이후로는 element를 써야 한다.<br/>

## Router( BrouserRouter)

```jsx
import { BrowserRouter as Router } from "react-router-dom";
```

Router는 history API를 사용해 URL(Link)과 UI(Route)를 동기화하는 라우터이다.<br/>
Router 종류는 BrouserRouter 외에도 여러 종류가 있다.<br/>
`<Router>` 컴포넌트는 위에 나온 `<Route>`와 `<Link>` 컴포넌트가 함께 유기적으로 동작하도록 묶어주는 역할을 한다.<br/>
`<Route>`와 `<Link>` 컴포넌트는 DOM 트리 상에서 항상 `<Router>`를 공통 상위 컴포넌트로 가져야 한다.
