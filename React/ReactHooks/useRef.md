# useRef

javascript에서 특정 DOM을 선택하는 역할은 대표적으로 getElementId가 있다.

리액트 프로젝트에서도 가끔 DOM 을 직접 선택해야 하는 상황이 발생하는데, 이때 useRef hook을 사용한다.
(ex.초기화버튼을 눌렀을 때 input에 포커스 잡기)

```jsx
import React, { useRef, useState } from "react";

export default function InputSample() {
  const [inputs, setInputs] = useState({ name: "", nickname: "" });

  const nameInput = useRef();

  const { name, nickname } = inputs;

  const onChange = (e) => {
    const { value, name } = e.target;
    setInputs({
      ...inputs,
      [name]: value,
    });
  };

  const onReset = () => {
    setInputs({
      name: ``,
      nickname: ``,
    });
    nameInput.current.focus();
  };

  return (
    <div>
      <input
        name="name"
        placeholder="이름"
        onChange={onChange}
        value={name}
        ref={nameInput}
      />
      <input
        name="nickname"
        placeholder="닉네임"
        onChange={onChange}
        value={nickname}
      />
      <button onClick={onReset}>초기화</button>
      <div>
        <b>값: </b>
        {name} ({nickname})
      </div>
    </div>
  );
}
```

useRef()를 사용해 Ref 객체를 만들고 이 객체를 우리가 선택하고 싶은 DOM에 ref값으로 설정. 그럼 Ref객체의 .current값은 우리가 원하는 DOM을 가르킨다.

위 예제에서는 onset함수에서input에 포커스하는 focus DOM API를 호출

console.log로 살펴보면 다음과 같다.

```js
console.log(nameInput);
//{current: input}

console.log(nameInput.current);
//<input name="name" placeholder="이름 value>
```
