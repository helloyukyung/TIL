# TSBasic

타입스크립트는 자바스트립트와 다른언어가 아니다.  
같은 자바스크립트이지만 개선사항이 있을 뿐!

## 변수 타입 지정

```ts
let 이름: string = "kim";

이름 = 123; // err
```

이 변수엔 string(문자) type만 들어올 수 있다.

## object 타입지정

```ts
let 이름: { name?: string } = { name: "kim" };
```

뒤에 ? 는 해당 변수가 옵션(들어올수도 안들어올수도 있음)으로 쓰일 수 있다는 것을 의미한다.

## Union type

```ts
let user: string | number = "kimyk";

user = 60;
```

다양한 타입이 들어올 수 있게 한다.

## Type alias

```ts
type Usertype = string | number;

let user: Usertype = "yk";
```

타입을 변수에 담아 쓰는것도 가능하다.

## 함수에 타입지정

```ts
function add(x: number): number {
  return x + 2;
}
```

파라미터 뿐만아니라 리턴되는 값의 type도 정의 가능하다.

위 함수는 파라미터로 number값을 받으며, return 값은 number

```js
type Member = [number, boolean];

let yukyung: Member = [123, true];
```

array에 tuple type(순서가 고정)

## object에 타입지정해야할 속성이 너무 많을 때

```js
type Member = {
  [key: string]: string,
};

let yukyung : Meber ={
    name :"kim",
    age:"23";
}
```

글자로 된 모든 object 속성의 타입은 string으로 지정
