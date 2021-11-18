# StyledComponents

styled-components문법을 사용해 Material UI component 스타일링 하는 법

```jsx
import { StylesProvider } from "@material-ui/core/styles";
import ArrowBackIcon from "@mui/icons-material/ArrowBack";

const BackIcon = styled(ArrowBackIcon)`
  :hover {
    color: white;
  }
`;

export default function StyledComponents() {
  return (
<StylesProvider injectFirst>
  <BackIcon sx={{ color: "#ff9966", fontSize: 36 }}>Styled Components</BackIcon>
</StylesProvider>;
  );
}

```

Material-UI의 StylesProvider 컴포넌트로 감싸주고 injectFirst props를 준다.
