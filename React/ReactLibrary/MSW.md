# MSW

데이터 모킹 라이브러리

RestAPI 와 GraphQL support

Mock Service Worker

Interception on the network Level(하이제킹)

## 모킹(mocking)

Mock(모의데이터)을 만들어서 활용하는 방식

통상적으로 data fetch 를 해야하는 경우 통신을 통해 응답을 내려주는 서버가 있어야 한다.

서버가 없는 경우 api요청으로 내려올 데이터를 프론트에서 모킹하거나 서버의 역할을 해주는 무언가가 필요하다.
(sercive worker, node server)

## Worker /Server

테스트는 브라우저에서 하는게 아니라 node환경에서 한다.

msw에서 제공하는 브라우저 방식은 브라우저에서 제공하는 service worker - api를 쓴것

node환경에서는 따로 브라우저워커 방식을 이용할 수 없으므로

node에 서버를 setup한다 (server.js)

테스트를 돌릴 때는 server.js mocker를 쓰고 브라우저에서 쓸때는 browser.js serviceworker를 쓴다.
