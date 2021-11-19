# Lottie

Lottie는 에어비앤비에서 개발한 라이브러리로 간단하게 벡터 애니메이션을 웹, 앱에 적용할 수 있게 만들어준다.
https://airbnb.design/lottie/

https://lottiefiles.com/

주로 웹에 사용되는 이미지는 래스터와 벡터로 구분되는데, 레스터(jpg, png)는 우리가 알고 있는 픽셀 개념이며 벡터(svg, ai)는 수학 방정식을 기반으로 점, 선, 곡선 등을 나타낸다.

래스터는 주로 사진 이미지에 적합하고, 벡터는 기호나 단순한 형태, 거대한 크기(해상도 저하가 없으므로)로 인쇄가 필요할 때 사용한다.

로티에 사용되는 파일은 백터의 애니메이션 버전이다(json). 백터 기반이다 보니 용량도 적고, 해상도 저하가 없다는 장점이 있다.

## 사용 code

```jsx
import React from "react";
import Lottie from "react-lottie";
import walkingDog from "./walkingDog.json";

const lottieOptions = {
  animationData: walkingDog,
  autoplay: true,
};

export default function LotttieDog() {
  return (
    <div>
      <Lottie
        options={lottieOptions}
        style={{ width: "180px", height: "360px" }}
      />
    </div>
  );
}
```
