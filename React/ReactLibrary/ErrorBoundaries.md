# Error Boundaries

UI의 일부분에 존재하는 자바스크립트 에러때문에 전체 어플리케이션이 중단되는 경우를 막기위해 쓰인다.

즉, error boundaries(에러경계)는 하위 컴포넌트 트리의 어디든지 에러를 기록하며 깨진 컴포넌트 트리대신 폴백 UI를 보여주는 React component다.

```ts
function App() {
  return (
    <ErrorBoundary FallbackComponent={Error}>
      <BrowserRouter>
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="signin" element={<Signin />} />
        </Routes>
      </BrowserRouter>
    </ErrorBoundary>
  );
}
```

만약 런타임에 문제가 있을 때 `Error`가 뜨게 됨
