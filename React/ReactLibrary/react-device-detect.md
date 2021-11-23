# react-device-detect

리엑트에서는 react-device-detect 라이브러리를 이용해 모바일 반응형 페이지를 만들 수 있다.

## BrowserView

BrowserView 태그를 이용해 PC에서만 렌더링 되는 컴포넌트를 만들 수 있다.

## MobileView

모바일에서만 렌더링 되는 컴포넌트를 만들 수 있다.

## isBrowser & isMobile

```jsx
export const drawerWidth = () => {
  if (isMobile) {
    return "100vw";
  }
  return "450px";
};
```

isBrowser & isMobile의 경우, if문을 사용해 브라우저 환경일 때와 모바일 환경 일 때를 구분하여 사용할 수 있다.
