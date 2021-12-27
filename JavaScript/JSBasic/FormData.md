# FormData

FormData는 ajax로 폼(form 태그)전송을 가능하게 해주는 FormDatat 객체를 말한다.

wordcheck 프로젝트에서 JSON 구조로 폼 데이터를 제출했는데 올바르지 않은형식이라고 에러가 났다.

form을 제출하면 action 속성에 의해 지정한 페이지로 이동하면서 데이터를 전송하게 되는데,  
FormData(ajax)는 반대로 제출버튼을 누르면 기본 폼동작은 e.preventDefault()로 멈추고, 페이지 전환 없이 데이터를 전송할 수 있다.

# json과 ajax차이

AJAX는 js,xml,html,json과 같은 다양한 데이터 형식을 사용해 서버와 데이터를 주고받을 수 있다.
JSON은 데이터 교환을 위해 AJAX에서 사용할 수 있는 데이터 열거 방식이다.

(+ ajax는 화면갱신 없이 클라이언트에서 자바스크립트를 이용해 변경되는 부분을 바꿔줄 수 있다.)
