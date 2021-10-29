Custom Hooks
====

Custom Hook이전에는 

```js
    const onChangeId = (e) => {
        setId(e.target.value);
    };
```
똑같은데 이름만 다른 함수를 Id, Password, NickName 3개씩이나 만들어야 했다. 
따라서 간결하게 custom hook을 사용하여 반복을 줄였다.

```jsx
    //custom hook을 사용하여 반복 줄임
    const useInput = (initvalue = null) =>{
        const [value,setter] =useState(initvalue);
        const handler = (e)=>{
            setter(e.target.value)
        }
        return [value, handler]

    }
    const [email, onChangeEmail]= useInput('')
    const [nickname, onchangeNickname] = useInput('')
    const [password, onChangePassword] = useInput('')
```
(setter: 지정한 속성 값의 변경을 시도할 때마다 함수를 호출)

useInput은 initvalue가 null(초기값이 null이므로)값이며 return으로 [value, handler]를 반환한다.

 입력```(<input onChange={onChangeEmail}/>)```값이 바뀔 때마다 onChangeEmail(made by 'useInput')이 실행됨