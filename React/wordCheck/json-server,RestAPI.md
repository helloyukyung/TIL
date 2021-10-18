json-server(라이브러리)
====
json-server란 짧은시간에 REST API를 구축해주는 라이브러리(공부용)

json-server를 통해 만들어둔 data.json 파일을 port 8000번으로 REST API server를 구축해봄 

REST api
====
 HTTP URI(Uniform Resource Identifier)를 통해 자원(Resource)을 명시하고, 
HTTP Method(POST, GET, PUT, DELETE)를 통해 해당 자원에 대한 CRUD Operation을 적용하는 것을 의미함

 웹 사이트의 이미지, 텍스트, DB 내용 등의 모든 자원에 고유한 ID인 HTTP URI를 부여함

<h3>CRUD Operation</h3>

- Create : 생성(POST)
- Read : 조회(GET)
- Update : 수정(PUT)
- Delete : 삭제(DELETE)
- HEAD: header 정보 조회(HEAD)

axios
----
위 CURD를 axios에서 사용할 수 있음 

- GET : axios.get(url[, config])
- POST : axios.post(url, data[, config])
- PUT : axios.put(url, data[, config])
- DELETE : axios.delete(url[, config])

일반적으로 axios를 쓰기위해서는 4가지 기본 Params(Method, Url, Data(optional), Params(optional, 사용자 번호에 따른 조회))를 axios에 알려줘야한다. 

```
axios({
    method: "get",
    url: "url",
    responseType: "type"
}).then(function (response) {
    // response Action
});
```
 POST 메서드에서 data를 전송하기 위해서는 url 밑에 data Object를 추가하면 된다.