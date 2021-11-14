# div와 span의 차이

### 1. 줄바꿈

Div는 줄바꿈이 되지만 span(inline 속성) tag는 옆으로 붙게된다.

```js
export default function CssPractice() {
  return (
    <>
      <div>div1</div>
      <div>div2</div>
      <div>div3</div>
      <span>span1</span>
      <span>span2</span>
      <span>span3</span>
    </>
  );
}

// 결과
div1;
div2;
div3;
span1span2span3;
```

### 2. 영역

텍스트를 표현할 때 div 는 사각형 박스로 구역을 정하지만 span 은 문장 단위로 지정한다.
