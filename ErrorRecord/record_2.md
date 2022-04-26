# Property 'target' does not exist on type '(event: ChangeEvent<HTMLSelectElement>) => void'.

```
Property 'target' does not exist on type '(event: ChangeEvent<HTMLSelectElement>) => void'.
```

select 태그의 onChange이벤트 함수에서 e객체의 타입을 'React.ChangeEventHandler<HTMLSelectElement>'로 지정해줬는데 target부분에서 에러가 났다.(킹니를 쓰면 에러가 안남,,)

## 해결 방법

```tsx
const [modelId, setModelId] = useState < number > 0;
```

target.value는 스트링으로 받아진다.
그런데 modelId의 type값은 number로 되어있어 에러가 난 것.

```
    console.log(typeof e.target.value) // string
```

따라서 useState의 type을 string으로 바꿔 해결했다.
