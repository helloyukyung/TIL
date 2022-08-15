## .module.css

css 모듈을 이용하면 css클래스 스타일의 유효범위를
React 컴포넌트로 제한할 수 있다.

Next에서 `.module.css` 파일을 import 방식은 아래와 같다.

```js
import classes from "./MeetupItem.module.css";

function MeetupDetail(props) {
  return (
    <section className={classes.detail}>
      <img src={props.image} alt={props.title} />
      <h1>{props.title}</h1>
      <address>{props.address}</address>
      <p>{props.description}</p>
    </section>
  );
}

export default MeetupDetail;
```

```css
.detail {
  text-align: center;
}
.detail img {
  width: 100%;
}
```

이를 통해 클래스 이름을 다른 컴포넌트와의 충돌 없이 사용할 수 있다.
