# QueryString

사용자가 입력데이터를 전달하는 방법 중 하나로,
url주소에 협의된 데이터를 파라미터를 통해 넘기는 것을 말한다.

query parameters(물음표 뒤 = 로 연결된 key value)를 url 뒤에 덧붙여 추가적인 정보를 서버측으로 전달한다.

그럼 서버에서는 endpoint 정보에서 추가적인 정보가 교집합된 데이터를 반환해준다.

- 엔드포인트주소 이후에 ?를 쓰는 것으로 쿼리 스트링이 시작된다.  
  (+엔드포인트 :요청을 받아 응답을 제공하는 서비스를 사용할 수 있는 지점)

- parameter = value 로 필요한 파라미터의 값을 적는다.

- 파라미터가 여려개일 경우 &을 붙여 여러개의 파라미터를 넘길 수 있다.

## EX

'수원'에서 '신도림'으로 최단 거리 경로 요청 url

요청 url: http://localhost:3000/paths?source=수원&target=신도림&type=DISTANCE

(endpoint : http://localhost:3000/paths)
