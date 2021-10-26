Axios
====
무료 api서버를 사용하여 Axios로 API 화면에 출력해보기 

<a href="https://github.com/yukyung123/TIL/blob/master/CS/Node.js%26API.md">설명 참고</a>

```js
import React, {useState} from 'react'
import axios from 'axios'
export default function AxiosApi() {

    //photos, setPhotos 비구조화 할당해줌
    let [photos, SetPhotos] = useState([]);

    // 통신 메소드 

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