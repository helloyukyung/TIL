서론 (?)
====
웹 개발에는 FE와 BE가 있다.
사용자 입장에서는 FE가 구현한 웹페이지를 보게 되며,
BE는 웹 내 DB를 관리한다.

예시로 네이버 홈페이지를 들어가보자. 
화면을 계속해서 보면 웹 안의 div들이 동적으로 변하는 것을 볼 수 있다. 
뉴스카테고리를 들어가 보더라도 div들은 시간대별로 계속 바뀐다. 

<b>그럼 Div 업데이트는 어떻게 이뤄질까?</b><br/>
 FE개발자가 하나하나 div컴포넌트 안에 입력을 해주나?는 당연히 아니다. <br/>
FE는 BE에게 API를 요청하여 데이터를 전송받아 웹페이지에 구현을 해준다.<br/>

----

<이전에 개념정리>

<b>node.js란?</b>
자바스크립트 런타임(실행환경)

node.js는 javescrpit언어(고급언어)륻 저급언어(컴퓨터가 인식하는 언어)로 변환시켜주는 실행환경을 제공한다.

npm: node.js 라이브러리 설치, 관리 프로그램(자바스크립트 패키지 쇼핑몰(?))<br/>
npx: node.js 라이브러리 설치하고 삭제까지 (ex. create-react-app)

npm init :node.js 환경을 세팅함 (package.json 파일이 생김)
package.json : 설치한 package들을 관리하는 파일 

----

다시 돌아와서,
API로 앱과 서버가 통신하기 위해서는 HTTP(Hyper Text Transfer Protocal)를 사용하게 된다.<br/>
 요청하고 싶은 목적에 따라 HTTP method를 사용해 API를 요청해줄 수 있다. 

기본적인 HTTP메소드 종류와 특징(리소스:데이터)

- GET : 리소스를 요청
- POST : 리소스를 등록
- PATCH : 리소스를 일부만 변경
- PUT : 리소스를 대체, 해당 리소스가 없으면 생성
- DELETE : 리소스를 삭제 

네트워크 상에서 API를주고받기 위해서는 HTTP프로토콜 Method를 사용한다.

AXIOS
====
이제 드디어 액시오스의 등장인데,<br/>
누군가(?) HTTP프로토콜 METHOD를 본인이 이용하기 쉽게 다듬어 "axios"라는 라이브러리를 만들어 npm에 배포한것이다. 


명령은 HTTP method와 같다.

<h2>axios 실습</h2>

1. 폴더 생성 

2. 폴더 안에 들어가서 git init 명령실행(package.json 생성)

3. npm install axios 액시오스 설치
    package.json을 보면 dependencies에 axios가 설치된것을 확인할 수 있음.
    이 파일은 axios에 의존(axios모듈을 사용하고 있다고 보자)

4. 새로 axiosTest.js 파일생성 

    https://jsonplaceholder.typicode.com/ 공짜로 제공해주는 사이트 

5. 파일내에 아래와 같이 입력

    todos: 리스트 ,1은 리스트 상세

```js
import axios from 'axios';


axios.get('https://jsonplaceholder.typicode.com/todos/1').then((Response)=>{
    console.log(Response.data);
}).catch((Error)=>{
    console.log(Error);
})

```

6. 터미널에서 Node axiosTest.js 명령하여 파일 실행 
```output
{ userId: 1, id: 1, title: 'delectus aut autem', completed: false }
```
<번외>

우리는 깃에 올릴 때 node_modules는 올리지 않음. <br/>
왜냐 그냥 다시 설치해주면 되니까 (용량낭비)

그래서 .gitignore파일을 보면 깃에 관리되지 않게 끔 제외되는 파일들을 입력해줄 수 있다.</br>
클론한 파일을 사용하고 싶다면, 그냥 터미널에 npm install 해주면 해당 git 파일 안에 있는 노드모듈이 다 설치될것이다.