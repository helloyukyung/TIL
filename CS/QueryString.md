# Query Parameter & Query String

Query Parameter 은 경로 뒤에 입력 데이터를 함께 제공하는 식으로 사용한다.

```
/detail_list/?contents="day1"&wrong_count=2
```

엔드포인트 주소 이후 ? 부분부터 query string이라고 하며,이부분에는 key, value 로 필요한 파라미터의 값이 들어간다.

(+엔드포인트 :요청을 받아 응답을
제공하는 서비스를 사용할 수 있는 지점)

파라미터가 여려개일 경우 &을 붙여 여러개의 파라미터를 넘길 수 있다.
