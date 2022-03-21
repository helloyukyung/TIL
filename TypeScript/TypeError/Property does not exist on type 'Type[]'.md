# Property 'name' does not exist on type 'OptionType[]'.

```ts
type PropTypes = {
  option: OptionType[];
};

type OptionType = {
  id: number;
  name: string;
  age: number;
};

function Form(props: PropTypes) {
  console.log("===>", props.option?.name);

  return <div>...</div>;
}
```

## 문제 원인

option의 OptionType이 배열이라 name값을 못 가져옴.

## 해결 1

```ts
type PropTypes = {
  option?: OptionType; //removed `[]`
};
```

배열 정의를 제거

## 해결 2

```ts
console.log("===>", props.option[index].name);
```

루프안에서 생성
