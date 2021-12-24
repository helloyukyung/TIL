# TypeError: Cannot read properties of undefined (reading 'nickname')

wordcheck 프로젝트 중 위와 같은 에러 발생

## 에러코드

```js
export function loginUser(dataToSubmit) {
  console.log("asdf", dataToSubmit);
  const formData = new FormData();
  formData.append("nickname", dataToSubmit.nickname);
  formData.append("password", dataToSubmit.password);
  const request = axios
    .post("url", formData)
    .then((response) => {
      console.log(response.data);
    })
    .catch((err) => {
      console.log("==>", err);
    });

  return {
    type: LOGIN_USER,
    payload: request,
  };
}
```

## 에러가 난 이유

정의가되지 않은 객체의 프로퍼티를 읽어내 에러가 발생한 것같다.  
dataToSubmit이 랜더링되었을 때 undifined인데 dataToSubmit의 nickname을 찾으려고 하니까 에러가 발생한 것

## 해결방법

`?` optional chaining 사용  
optional chaining 연산자는 undefined 이나 null 값을 예외처리해준다.

```js
formData.append("nickname", dataToSubmit?.nickname);
formData.append("password", dataToSubmit?.password);
```
