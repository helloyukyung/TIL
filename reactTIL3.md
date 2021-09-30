React 공식문서로 디테일 잡기 (고급)
====
Hooks
----
Class의 단점을 보완하면서 라이프사이클 등과 관련된 함수를 재사용 가능토록 함

- Hook 사용 규칙 
1.  최상위 (at the top level)에서만 Hook을 호출해야한다. 반복문, 조건문, 중첩된 함수 내에서 Hook을 실행하면 안된다. 
2. Functional Component와 custom Hook 내에서만 호출해야 한다.

Hooks1 ( 정리 )
- Hooks등장 -> class의 단점 보완/ 재사용성 강화 
- Hook 사용 규칙 -> 최상위 /함수형 컴포넌트 / custom Hook 
- Class의 state -> 훅을 먼저 배웠기에 고민할 필요 x

Effect Hook 
----
데이터 가져오기, 구독 설정하기, 수동으로 리액트 컴퍼넌트의 DOM을 수정하기 

- componentDIdMount + componentDidUpdate
= useEffect(()=>{});

이전 ReactClassComponent
```jsx
import React, { Component } from 'react'

export default class EffectHook extends Component {
    constructor(props) {
        super(props)
        this.state ={
            count : 0
        };
    }
    componentDidMount() {
        document.title =`You clicked ${this.state.count}times`
    }
    componentDidUpdate() {
        document.title =`You clicked ${this.state.count}times`
    }


    render() {
        return (
            <div>
                <p>You clicked {this.state.count}times</p>
                <button onClick={()=> this.setState({count: this.state.count + 1})}>Click me</button>
                
            </div>
        )
    }
}
```
위 코드에서 class 안의 두 개의 생명주기 메서드에 같은 코드가 중복

Use Effect Hook 사용 
```jsx
import React, { useEffect, useState } from 'react'

export default function EffectHook() {

    const [count, setCount] = useState("")

    useEffect(()=>{
        document.title =`You clicked ${count} times`
    }) 
    return (
        <div>
            <p>You clicked {count}times</p>
            <button onClick={()=> setCount(count + 1)}>Click me</button>
        </div>
    )
}
```



- 구독과 정리 
ComponentDidMount & componentWillUnmount
= useEffect 하나에서 처리

- Effect가 업데이트 시마다 실행되는 이유? 

-> (Class 메서드가 관련없는 로직들은 모아놓고, 관련이 있는 로직들은 여러개의 메서드로 나누어 놓는 경우가 있었다)

componentDidMount / componentDidUpdate /componentWillUnmount 

이에 대한 해결책으로 표현을 하나로 합치고, 버그를 방지하기 위해!

- Effect를 건너뛰어 성능 최적화하기? 


이전에는 

componentDidUpdate(prevProps, prevState) {}

이제는<br/> 
dependency array로 주시하고 싶은 값을 입력 <br/>
특정 state의 변경에만 반응하게
<br>

Hook2 (정리)
----
- useEffect -> 데이터 fetch/ 구독 /Dom 수정 
- Clean up -> 구독과 구독해지를 한 공간에서 
- dependency array -> 필요한 변경시에만 effect 실행


Custom Hooks
----
컴퍼넌트들에 중복되는 Hook로직을 묶어서 재사용 하도록 함 

Hook에서 Hook으로 정보 전달 가능 

Reducer
----

using use state
```jsx
import React, { useState } from 'react'

export default function State() {
    const initialCount = 0;
    const [count , setCount] =useState(initialCount)

    
    return (
        <div>
            Count {count}
            <button onClick={()=> setCount(prev => prev-1)}>-</button>
            <button onClick={()=> setCount(prev => prev+1)}>+</button>
        </div>
    )
}
```

using reducer
```jsx
import React, { useReducer } from 'react'

export default function State() {
    const initialState = {count :0, name: 'yukyung'};

    function reducer(state, action) {
        switch(action.type){
            case 'reset':
                return {initialState};
            case 'increment':
                return {count: state.count+1 ,name:'amy'};
            case 'decrement':
                return {count: state.count-1, name:'jimmy'};
            default:
                throw new Error();
        }
    }
    
    const [state, dispatch] = useReducer(reducer, initialState)
    
    return (
        <div>
            Count: {state.count}
            Name: {state.name}
            <button onClick={()=> dispatch({type:'reset'})}>reset</button>
            <button onClick={()=> dispatch({type:'decrement'})}>-</button>
            <button onClick={()=> dispatch({type:'increment'})}>+</button>
        </div>
    )
}
```
reducer: 여러 상태를 한번에 관리할 수 있음 

Hooks3(정리)
----
- useState : 이전 값을 인자로 / 초기화 지연(함수)
- useEffect : 의존성 배열, 안주거나/[]/[a,b]
- useLayoutEffect : useEffect와 유사 모든 DOM변경 후 브라우저가 화면을 그리기 이전 시점에 동기적으로 수행됨 
- useReducer: useState 대체 state/reducer/ action 
- useContext : Context강의에서 볼 것 
- useCallback & useMemo : 메모이제이션 강의에서 볼 예정
- useRef : current라는 상자. 내용의 변경은 알려주지 않음 .콜백 ref사용 

<br>

- Custom Hook -> 컴포넌트들에 반복되는 Hooks 묶기 
- 다양한 Hooks -> 필요한 타이밍에 참고해서 사용 

<br>

Composition 
----
<b>Composition(합성) vs Inheritance(상속)</b>

React는 강력한 합성 모델을 가지고 있으며, 상속대신 합성을 사용하여 컴포넌트 간에 코드를 재사용하는 것이 좋다. 


컴포넌트에 다른 컴포넌트를 담기(Children/custom(left,right))

특수화 (Specialization)






















