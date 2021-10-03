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


Composition은 컴포넌트에 다른 컴포넌트를 담기

담는 방법: (Children/custom(left,right))

특수화 (Specialization)

typeof -> type check 

확장성 -> 다양한 상황을 품을 수 있도록 

HOC(Higher Order Component)
----

고차 컴포넌트(HOC)는 컴포넌트를 가져와 새 컴포넌트를 반환하는 함수 

컴포넌트 로직을 재사용하기 위한 React의 고급기술 


```jsx
const EnhancedComponent = higherOrderComponent(WrappedComponent)
```

Memoization 
---- 
메모이제이션: 컴퓨터 프로그램이 동일한 계산을 반복해야 할 때, 이전에 계산한 값을 메모리에 저장함으로써 동일한 계산의 반복 수행을 제거하여 
프로그램 실행속도를 빠르게 하는 기술이다. 



- React.memo 

동일한 props로 렌더링을 한다면, React.memo를 사용하여 성능 향상을 누릴 수 있다. 
memo를 사용하면 React는 컴포넌트를 렌더링하지 않고 마지막으로 렌더링된 결과를 재사용한다.


- profiler

React 애플리케이션이 렌더링하는 빈도와 렌더링 "비용"을 측정 <br/>
메모이제이션과 같은 성능 최적화 방법을 활용할 수 있는 애플리케이션의 느린 부분들을 식별

-하나만 추가되는데 모든 component가 재실행 되는것을 볼 수 잇음
부모의 dependency가 바뀌면서 자녀들도 다 영향,, 
 ->  memoization(그려진것들은 다시 씀), 비효율을 줄일 수 있다 


- usecallback()<br/>
-특정한 함수를 받아서 호출
함수를 memoization 할 수 있게끔 도와줌 

- usememo()<br/>
어떤 값을 return 하는 함수 
계산을 통해 만들어진 특정한 값,변수를 memoization

-예제에서 likes가 10 이상이 아니면 bad이라는 rate()를 만들어 넣었는데 그 좋아요 값은 계속 바뀌지 않아서 계속 bad를 반환했음
그랬을때, 처음 memo했을때 set해 놓은 memoization값을 계속 사용하여 component가 리랜더링이 되더라도 비효율이 발생되지 않았음 

-useCallback(fn,deps)는 useMemo(()=>fn, deps)


Memoization (정리)
----
React.memo -> HOC/ Props 비교하여 메모 
Profiler -> 리액트 성능 분석 도구 
callback -> useCallback 
value -> useMemo

-------

Context
----
컴포넌트 트리를 넘어 데이터를 공유할 수 있는 방법<br/>
Props drilling,,,문제를 해결(children을 계속 만들면 계속 props를 전달해줘야 하는)<br/>
context를 이용하면 단계마다 일일이 props를 넘겨주지 않고도 컴포넌트 트리 전체에 데이터를 제공할 수 있다.

<b>언제 context를 써야할까?<b><br/>
context는 React component 트리 안에서 전역적이라고 볼 수 있는 데이터를 공유할 수 있도록 고안.
그러한 데이터로는 현재 로그인한 유저, 테마, 선호하는 언어 등이 있음 

밖에 있을 때는 default값, provider로 감싸진 건 provier의 값을 봄


Context(정리)
----
컴포넌트 트리 제약 -> Props drilling의 한계 해소 
재사용성 -> Context를 사용하면 재사용하기 어려움 (context안에 감싸져 있어야 하므로)
API -> createContext / Provider / Consumer
useContext -> Consumer 대체 

----

Portals 
----
DOM 계층 구조 바깥에 있는 DOM 노드로 자식을 렌더링하는 최고의 방법

createPotal -> 부모 컴포넌트 DOM 트리로부터 벗어남 

이벤트 -> Portal에 있더라도 Event는 트리로 전파