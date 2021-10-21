flexbox froggy remind
====
먼저 flex box를 만들어줌
```
.flex_container {
    display:flex;
}

```
flex 속성이 적용된 요소는 flex container.

 flex container의 자식(자식요소)은 flex item.

 부모 요소와 자식 요소에 정의하는 속성 구분
----

- flex container 속성: flex-direction, flex-wrap, justify-content, align-items, align-content

- flex item 속성: flex, flex-grow, flex-shrink, flex-basis, order

<br>
<br>

-----


<h3> ex. justify-content</h3>

- flex-start: 요소들을 컨테이너의 왼쪽으로 정렬
- flex-end: 요소들을 컨테이너의 오른쪽으로 정렬
- center: 요소들을 컨테이너의 가운데로 정렬
- space-between: 요소들 사이에 동일한 간격을 둠
- space-around: 요소들 주위에 동일한 간격을 둠 

```
#pond {
  display: flex;
justify-content: center;
}
```



style-component
====


가변스타일링
----
1. 바꾸고 싶은 css속성이 하나인 경우

```jsx
const Label = styled.label`
  padding-right:${props=>props.paddingRight || "0px"};
  font-size : 20px;
`
```
회원가입창의 label과 input을 맞춰주기 위해서 email의 label에만 padding-right를 바꿔주고 싶었다.

-> 기본값은 0px이되 login label 에서는 props 값을 바꿔줄 수 있었음. 재사용성이 매우좋음
```jsx
<Label paddingRight="27px">E-mail : </Label>
```

2. 바꾸고 싶은 css속성이 하나가 아니라 여러개일 경우 
```jsx
import React from "react";
import styled, { css } from "styled-components";

const StyledButton = styled.button`
  padding: 0.375rem 0.75rem;
  border-radius: 0.25rem;
  font-size: 1rem;
  line-height: 1.5;
  border: 1px solid lightgray;

  ${(props) =>
    props.primary &&
    css`
      color: white;
      background: navy;
      border-color: navy;
    `}
`;

function Button({ children, ...props }) {
  return <StyledButton {...props}>{children}</StyledButton>;
}
```
Styled Components에서 제공하는 css함수를 사용해서 여러개의 CSS속성을 묶어서 정의 .

&&(논리곱) 연산자를 사용해서, primary prop이 존재하는 경우에만 css로 정의된 스타일이 적용
