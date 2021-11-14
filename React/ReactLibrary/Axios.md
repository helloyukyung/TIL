Axios
====
무료 api서버를 사용하여 Axios로 API 데이터를 화면에 출력해보기 

<a href="https://github.com/yukyung123/TIL/blob/master/CS/Node.js%26API.md">참고</a>


```js
import React, {useState} from 'react'
import axios from 'axios'
export default function AxiosApi() {

    //photos, setPhotos 비구조화 할당
    const [photos, SetPhotos] = useState([]);

    // 통신 메소드 
    // api 요청 하고 SetPhotos로 photos에 값을 할당
    function searchApi() {
        const url ="https://jsonplaceholder.typicode.com/photos";
        axios.get(url)
        .then(function(response) {
            SetPhotos(response.data);
            console.log("성공")
        })
        .catch(function(error){
            console.log("실패");
        })
    }
    // 조회 데이터가 존재할 경우 
    if (photos.length > 0) {
        return (
            photos.map(photo => (
                (photo.id <10 ) ? (
                    <div key={photo.id}>
                        <img src={photo.thumbnailUrl} alt="img"/>
                        <p>title : {photo.title}</p>
                    </div>) 
                    : null
            ))
        )
    } else { // 조회 데이터가 존재하지 않을 경우 
        return (
            <div>
                <button onClick={searchApi}> 불러오기</button>
            </div>
        )

    }
}

```

응답 Schema 
----
axios 요청에 따른 응답결과는 응답 데이터 외에도 다양하게 출력 가능 

<a href="https://yamoo9.github.io/axios/guide/response-schema.html">참고</a>

- responce.data : 응답 데이터 
- responce.status :서버응답의 HTTP상태코드 
- responce.statusText: 서버응답으로부터의 HTTP상태 메세지

```js

const url ="https://jsonplaceholder.typicode.com/photos";
axios.get(url)
.then(function(response) {
    console.log(response.data)
    console.log(response.status)
    console.log(response.statusText) // 빈값ㅜ
})
.catch(function(error){
    console.log("실패");
})

```


API 연동
----
- useState를 이용해서 요청 상태를 관리
- useEffect를 사용하여 컴포넌트가 렌더링되는 시점에 요청을 시작 




