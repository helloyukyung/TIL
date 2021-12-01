# Redux

어플리케이션의 state를 관리하고 업데이트 해주는 상태관리 라이브러리.

## Redux가 필요한 이유

state를 부모에서 만들면 자식에게 계속 props로 계속 전송 전송해줘야 한다.(계속 중첩되면 복잡해짐 )

리덕스는 일일히 prop로 전달해주지 않아도 된다.
리덕스는 'state 보관함'(store.js)-> state를 직접 꺼내 쓸 수 있다.

상태 관리가 용이하다.(state관리)
state상태를 변경하고 싶을 때
'state 보관함'
에

```js
var 체중 = 100;

if (action.type === "증가") {
  state++;
  return state;
} else if (action.type === "감소") {
  state--;
  return state;
} else {
  return state;
}
```

component들은 몸무게 state를 달라고 부탁하면 됨(수정요청만 가능)

이렇게 모여져있어 버그가 일어났을 때 추적이 쉬움

## Redux 사용방법

컴포넌트에서 state 수정요청(reducer에서 만든)을 하려면 dispatch를 쓴다.

```js
const 꺼내온거 = useSelector((state) => state);
const dispatch = useDispatch();

return (
  <div>
    <p>나의 심각한 몸무게는 : {꺼내온거}</p>
    <button onClick={()=>{dispatch({type:'증가'})}}>더하기</butoon>
  </div>
);
```
