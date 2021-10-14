Router
----
리액트의 SPA 구현에 쓰이는 react-router-dom 
-SPA(single page application)은 화면의 header나 footer, sidebar등 다시 로드해도 변함이 없는 부분들은 그대로 유지한 채 변경되는 부분의 데이터만 가져와서 수정하는 웹사이트를 의미함 

해당 요청에 맞는 컴포넌트만 라우팅하여 부분적으로 랜더링 

 BrowserRouter와 HashRouter
----

react-router-dom의 라우터는 BrowserRouter와 HashRouter 두가지가 있음

BrowserRouter는 HTML5의 history API를 활용하여 UI를 업데이트하고,

HashRouter는 URL의 hash를 활용한 라우터입니다. (정적인(static)페이지에 적합)

보통 request와 response로 이루어지는 동적인 페이지를 제작하므로 BrowserRouter가 보편적으로 쓰임

Route
----
요청받은 pathname에 해당하는 컴포넌트를 렌더링

Switch
----
path의 충돌이 일어나지 않게 Route들을 관리

<b>Swtich</b> 내부에 <b>Route</b>들을 넣으면

요청에 의해 매칭되는 Route들이 다수 있을 때에 제일 처음 매칭되는 Route만 선별하여 실행하기 때문에 충돌 오류를 방지해주며, Route간에 이동 시 발생할 수 있는 충돌도 막아줌

(path와 매칭되는 Route가 없을 때에 맨 밑에 default Route의 실행이 보장됨)


