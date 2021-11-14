# FlexBox

flexbox는 행과 열 형태로 항목 무리를 배치하는 일차원 레이아웃 메서드를 말한다.

## 1. 페이지 전체 color을 div color로 바꿔보기

그냥 div값에 `height100%, background-color:green`를 넣어준다고 페이지 전체가 바뀌지 않는다.<br/>
그 이유는 div 상위 부모의 height를 정해주지 않았기 때문이다.<br/>
따라서 reset.css에 다음과 같이 height, width 를 설정해준다.<br/>

```
// in reset.css

html,
body {
height: 100%;
width: 100%;
}
#root {
height: 100%;
width: 100%;
}
```

그 다음 css 를 먹여주면 완벽

```
//in src/pages/Css/index.js

const Container = styled.div`
  height: 100%;
  background-color: green;
`;

export default function CssPractice() {
  return (
    <>
      <Container>colorChangediv</Container>;
    </>
  );
}


}
```

(+ 만약 Container위에 div부모를 추가한다면 추가한 div의 heigh값도 설정해줘야함 )

## 2. Container의자식 Div를 정중앙 배치 시켜보기

```js
export const Container = styled.div`
  display: flex; // use flexbox method
  flex-direction: row; // flex direction method를 row로 지정
  justify-content: center; // 가로축을 기준으로 content 좌우를 center로 지정 (flex-direction에 따라 row center, col center?바뀜)
  align-items: center; // 세로축을 기준으로 content 좌우를 center로 지정 (flex-direction에 따라 row center, col center?바뀜)
  text-align: center; // 글자 가운데 정렬

  height: 100%;
  background-color: green;
`;

const Div = styled.div`
  background-color: pink;
  height: 100px;
  width: 100px;
`;
export default function CssPractice() {
  return (
    <>
      <Container>
        <Div>Center</Div>
      </Container>
    </>
  );
}
```

## 3. Div2를 Div의 좌측 하단에 배치시키기

```jsx
import Container from "./index.js";
//다른 파일에서 styled component를 불러올 때 다음과 같이 import

const Div = styled.div`
  display: flex;
  flex-direction: row;
  justify-content: lett;
  align-items: flex-end;
  background-color: pink;
  height: 100px;
  width: 100px;
`;

const Div2 = styled.div`
  background-color: white;
  height: 50px;
  width: 50px;
`;

export default function CssPractice() {
  return (
    <>
      <Container>
        <Div>
          <Div2>bottom left</Div2>
        </Div>
      </Container>
    </>
  );
}
```
