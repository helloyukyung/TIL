Mixed Content
====
http - https 간 네트워크 이슈

최신 브라우저에서는 보안문제로 https 페이지에서 http리소스를 요청할 수 없다. 

서버 api 는 http, 깃허브 배포 페이지는 https

 (리엑트 개발서버는 http라서 개발단계에서는 잘 수신된것;))


에러 메세지 
====
```
xhr.js:210 Mixed Content: The page at 'https://yukyung123.github.io/gachigagae/' was loaded over HTTPS, but requested an insecure XMLHttpRequest endpoint '{서버}'. This request has been blocked; the content must be served over HTTPS.
```
