# Library Import Way

라이브러리를 불러오는 방법

```jsx
import Drawer from "@material-ui/core"

const Drawer = () => {
    ???
}
```

기본적으로는 위와같이 불러올 수 있지만 내가 컴포넌트 이름을 Drawer로 지정 했을 때는 이름이 겹칠 수 있다.  
내가 component의 이름을 바꾸고 싶지 않은 경우 아래와 같이 쓸 수 있다.

```jsx
import { Drawer as MUIDrawer } from "@material-ui/core";

or;

import MUIDrawer from "@material-ui/core/Drawer";

const Drawer = () => {
  <MUIDrawer></MUIDrawer>;
};
```
