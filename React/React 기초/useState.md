
useState
====
<h2>useState가 const 를 사용하는 이유</h2> 

```js
const [id, setId] = useState('')
```
useState 를 사용하면 setData로 값이 재할당 되는데 왜 let(변수;변하는 값)이 아닌 const(상수;변하지 않는 값)를 쓸까 궁금했다.<br/>
(사실 그냥 const라고만 알고 있었는데, 예제를 보는데 let을 쓰길래 궁금해짐)

 component가 rendering되면 함수가 다시 실행되는데 이때 새 scope(범위)를 만들고 새 id 변수를 만드므로, 이전 id변수랑은 상관이 없어지게 된다(랜더링 되면서 setId에 의해 값이 바뀌었을 때, 새로운 값이 지정됨). <br/>
 그리고 const 로 선언된 id변수는 동일한 범위에서 다시 할당되는 것을 막을 수 있다. 

