# Redux

어플리케이션의 state를 관리하고 업데이트 해주는 (전역)상태관리 라이브러리.

구성요소 : Store /Reducer /Action /Selector

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

component들은 몸무게 state를 달라고 부탁하면 된다.(수정요청만 가능)

이렇게 모여져있어 버그가 일어났을 때 추적이 쉽다.

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

## redux/toolkit

복잡한 리덕스 스토어를 편하게 사용하게 만들어준다.

Redux 라이브러리들 조합(immer/saga/thunk/reselect)

### createAsyncThunk 

redux toolkit 만으로 비동기 처리를 쉽게 할 수 있다. 
이전에는 useEffect로 비동기처리 but, createAsyncThunk를 사용하면 전역적으로 비동기 처리가 가능하다.

---
redux 3가지 규칙 
1. 하나의 어플리케이션에 하나의 스토어 

2. 상태는 읽기전용 
불변성을 유지해야한다(내부적으로 데이터가 변경 되는 것을 감지하기 위해 shallow equality 검사를 하기 때문) 

3. 변화를 일으키는 함수인 리듀서는 순수한 함수여야 한다. 

- 리듀서 state +action를 파라미터로 받아 => newstate
- 이전의 상태는 건들이지 않고 변화를 일으킨 새로운 상태객체를 만들어 반환 
- 똑같은 파라미터로 호출된 리듀서 함수는 언제나 똑같은 결과값을 반환해야한다.