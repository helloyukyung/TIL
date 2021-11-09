CORS 
====
CORS(Cross-Origin Resource Sharing, 교차 출처 리소스 공유)


CORS는 추가 http헤더를 사용해, 한 출처에서 실행중인 웹 어플리케이션이 다른출처의 자원에 접근할 수 있는 권한을 부여하도록 브라우저에 알려주는 체제.

XML HttpRequest와 FetchAPI(데이터를 전송받고 처리하는 통신객체)는 동일한 출처정책을 따르는데, 
 위 API를 사용하는 웹 애플리케이션은 자신의 출처와 동일한 리소스만 불러오는게 가능하며, 다른 출처의 리소스를 불러오려면 그 출처에서 올바른 CORS헤더를 포함한 응답을 반환해야 한다. 

CORS error
----
내 로컬 (localhost:3000)에서 axios를 사용해 서버(http://sulrae.com/gachigagae-admin/)에서 api를 호출해 데이터를 가져오려고 했으나 CORS 에러발생

```
gachigagae:1 Access to XMLHttpRequest at 'http://sulrae.com/api/shop' from origin 'http://localhost:3000' has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header is present on the requested resource.
```

서로 다른 출처, 즉 나는 로컬, 서버는 브라우저(외부서버)로 되어 있어 보안상의 이유로 차단을 당한것 같다. 

(+ useEffect 사용해서 axios호출을 했는데 dependency array를 [] 로 해놔서 api를 계속 호출해서 서버가 죽었다...⭐)

----

HTTP HEADER: 클라이언트와 서버가 요청 또는 응답으로 부가적인 정보를 전송