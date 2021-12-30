# hook을 사용하면서 발생한 에러

## 에러메세지

```
React Hook "useEffect" is called conditionally. React Hooks must be called in the exact same order in every component render. Did you accidentally call a React Hook after an early return?`
```

## 에러코드

```jsx
export default function Home() {
  const [cards, setCards] = useState([]);
  const cookies = new Cookies();
  const CookieToken = cookies.get("Token");

  if (!CookieToken) {
    return <Navigate to="/login" />;
  }
  useEffect(() => {
    if (CookieToken) {
      axios
        .get("http://52.78.37.13/api/words/", {
          headers: {
            Authorization: CookieToken,
          },
        })
        .then((response) => {
          setCards(response.data);
        })
        .catch((error) => {
          console.log(error);
        });
    }
  }, []);
  ...
```

에러가 발생한 이유는 훅이 조건부로 설정되었기 때문이라고 한다.

함수를 실행하면서 hook 선언 전에 조건을 통해 먼저 종료가 되면 안된다.  
나는 위에 토큰이 없으면 login페이지로 넘어가게 해놨던 것 ..

```jsx
export default function Home() {
  const [cards, setCards] = useState([]);
  const cookies = new Cookies();
  const CookieToken = cookies.get("Token");

  useEffect(() => {
    if (CookieToken) {
      axios
        .get("http://52.78.37.13/api/words/", {
          headers: {
            Authorization: CookieToken,
          },
        })
        .then((response) => {
          setCards(response.data);
        })
        .catch((error) => {
          console.log(error);
        });
    }
  }, []);


  if (!CookieToken) {
    return <Navigate to="/login" />;
  }
  ...
```

순서를 바꿔주자 해결되었다.

## hook의 2원칙

1. 훅은 최상위에서만 선언되어야한다.

- 반복문, 조건문 혹은 중첩된 함수 내에서 훅을 호출하면 안된다.
- 만약 조건부로 훅을 쓰고 싶다면 hook 내부에 선언해야한다.

2. 오직 React함수 내에서만 hook을 호출해야 한다.
