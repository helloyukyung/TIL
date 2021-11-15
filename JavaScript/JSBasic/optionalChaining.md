# Optional Chaining

옵셔널 체이닝(optional chaining) ?.을 사용하면 프로퍼티가(값이) 없는 중첩 객체를 에러 없이 안전하게 접근할 수 있다.

?.은 ?.'앞’의 평가 대상이 undefined나 null이면 평가를 멈추고 undefined를 반환한다.

```js
let user = {}; // 주소 정보가 없는 사용자

//이전에는 && 연산자를 사용 -> 코드가 길어짐(단점)
user && user.address && user.address.street; //undefined, 에러가 발생하지 않음

//Optional Chaining
alert(user?.address?.street);
```
