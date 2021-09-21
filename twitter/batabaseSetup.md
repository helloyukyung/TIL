database setup 

Cloud Firestore의 database는 NoSQL database이다.
NoSQL은 상당히 유연하고 규칙도 많이 없어 사용하기 쉬움, 그렇지만 규칙이 없는 만큼 제한되는 부분도 존재 
(다른 형태의 데이터 베이스로는 SQL database
많은 규칙과 관습이 존재 old system 하지만 그만큼 자유도 존재)

firestore,(NoSQL)이 가지는 특징 
1. collection ,document이라고 불리는 것을 가지고 있음
collection = 폴더와 같음 
document = 컴퓨터에 있는 문서와 같음 ,(doc, txt)

-각 collection 은 document 들을 가지고 있음,(documents의 그룹) 



## on code
<b>in fbase.js</b>

import { getFirestore } from "firebase/firestore";
export const dbService = getFirestore();

<b>in Home.js</b>

const docRef = await addDoc(collection(dbService, "kweets"), {
kweet,
createdAt: Date.now(),
});
console.log("Document written with ID: ", docRef.id);
} catch (error) {
console.error("Error adding document: ", error);
}

setKweet("");
};
const onChange = ({ target: { value } }) => {
setKweet(value);
};