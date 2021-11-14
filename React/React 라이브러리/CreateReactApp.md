# Create React App

```
//install
npx install create-react-app
```

### npm이 아닌 npx?

먼저, npm과 npx를 구분하지 말 것!<br/>
npx는 npm에서 제공해 주는 하나의 '도구'다.<br/>
자세하게 말하자면, 일회성으로 원하는 패키지를 npm레지스트리에 접근해 실행시키고 설치시켜주는 '실행 도구(Package Runner)'를 말한다.<br/>

---

## Create React App 이란

---

Create React App은 react의 Boilerplate(보일러 플레이트)다.<br/>
terms에서는 보일러 플레이트를
`변경이 거의 또는 전혀 없이 많은 곳에 포함되어야 하는 코드 섹션`라고 정의하고 있다.<br/>
즉 react project를 시작할 때, 기본적으로 많이 쓰이는 기능들을 create-react-app에 모아놓은 것이다.<br/>
CRA이 마냥 유용할 것 같지만, 실제로 React 프로젝트를 시작할 때, 불필요한(안 쓰는) 기능들이 기본적으로 설치되어 있을 수 있다는 단점 또한 존재한다.<br/>

---

## Create React App의 기본구조

---

### node_modules/

외부 모듈을 설치(ex. npm i axios)하면 node_modules 폴더에 다운로드 된다.<br/>
그리고 설치된 외부 모듈을 import 하면 Node.js는 node_modules에서 해당 모듈을 찾는다.<br/>

---

### public/

정적 파일들이 위치 (index.html) <br/>
해당 폴더 내의 파일들은 index.html에서만 사용될 수 있다.<br/>

#### index.html

서버에서 읽고 브라우저가 표출하는 파일이다.<br/>
index.js 에서 렌더링 된 결과가 표시된다.<br/>
해당 이름을 바꾸는 것은 권장하지 않는다. (서버 변경이 필요)<br/>

#### manifest.json

웹앱 메타 데이터.<br/>
홈 화면에서 보여지는 앱 이름, 아이콘, 디스플레이 유형을 설정할 수 있다.<br/>

(메타 데이터 : 다른 데이터를 설명해주는 구조화된 데이터<br/>
ex.핸드폰 갤러리에 사진 정보를 보면 사진을 찍은 날짜, 해상도 등을 확인할 수 있다.)

#### robots.txt

웹 크롤러를 위한 정보 <br/>
크롤러에게 색인화(찾아볼 수 있게 하는(?))할 수 있는 페이지와 허용되지 않는 페이지를 알려준다.<br/>

---

### src/

src : source의 약어<br/>
src/ 내부에 위치한 파일들이 webpack에 의해 processed된다.<br/>

( webpack: 오픈 소스 자바스크립트 모듈 번들러 ) <br/>
( 모듈 번들러: 웹 애플리케이션을 구성하는 자원(HTML, CSS, Javscript, Images 등)을 모두 각각의 모듈로 보고 이를 조합해서 병합된 하나의 결과물을 만드는 도구 )

#### index.js

해당 파일의 이름은 바꾸지 않는다(index.html과 마찬가지로).<br/>

```
ReactDOM.render(
    <App />,
    document.getElementById("root")
);

```

ReactDom이 App componet를 document 내 id 값이 root인 태그안에 랜더링한다.

#### App.js

root 가 되는 리액트 컴포넌트<br/>
컴포넌트를 정의(실제 화면에서 표시되는 내용이 여기에서 정의된다.)<br/>
해당 폴더에서 네비게이팅이 이루어진다.<br/>

위 파일들을 정리해서 보면 index.html > index.js > app.js 순으로 그려진다.<br/>

#### package.json

프로젝트의 메타데이터<br/>
프로젝트의 종속성을 처리하고 패키지매니저가 프로젝트를 식별할 수 있는 정보와 프로젝트 설명, 버전, 라이센스 정보 등 기타 메타데이터를 제공한다.<br/>
ex. axios(library) 설치시 package.json에 axios의 depandencies와 해당 library의 버전이 표시된다.<br/>
