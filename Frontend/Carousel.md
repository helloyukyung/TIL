# Carousel

Carousel 은 슬라이드의 형태로 순환하며 이미지, 영상 등의 콘텐츠를 노출하는 UI 를 말한다.  
사전적 의미로는 회전목마라고 나온다(빙빙 돌아가는, 순환하는 슬라이드를 의미하는 것 같다).

## react-material-ui-carousel

같이가개에서는 위 라이브러리를 사용하여 상세 리스트의 carousel을 구현하였다.

```jsx
import React from "react";
import { Paper } from "@mui/material";
import Carousel from "react-material-ui-carousel";
import { PhotoImg } from "../pages/Sidebar/DetailStyled";
import { StylesProvider } from "@material-ui/core/styles";
import styled from "styled-components";

const MyCarousel = styled(Carousel)`
  width: 450px;
  height: 270px;
`;

export default function Pictures({
  shop_id,
  image1,
  image2,
  image3,
  image4,
  image5,
}) {
  const images = [image1, image2, image3, image4, image5];

  return (
    <StylesProvider injectFirst>
      <MyCarousel>
        {images.map((img) => (
          <Paper>
            <PhotoImg alt={shop_id} src={img} />
          </Paper>
        ))}
      </MyCarousel>
    </StylesProvider>
  );
}
```
