# Primitive Types

오브젝트와 레퍼런스 형태가 아닌 실제 값을 저장하는 자료형
프리미티브 형의 내장 함수를 사용 가능한 것은 자바스크립트 처리 방식 덕분

es5기준 6가지

1. boolean
2. number
3. string
4. null
5. undefined
6. Symbol (ECMAScript5)

```js
let name = "mark";
name.toString();
```

```js
true;
("hello");
3.14; // number타입의 서브타입(3.14)
null;
undefined;
```

literal 값으로 primitive 타입의 서브타입을 나타낼 수 있다.
`true`는 primitive 타입 boolean의 서브타입이다.

```js
new Boolean(false);
// Boolean {false}
new String("hello");

new Number(3.14);
```

자바스크립트에서는 primitive타입 boolean을 위와 같은 래퍼객체로 만들 수 있다.

```js
typeof new Boolean(false);
//"object"
```

위는 '객체'이므로 object 형태로 나오게 된다.
( type을 나타내지 않는다는 소리로 말한 듯)

## Type Casing

- Typescript의 핵심 primitive type는 모두 소문자
- 앞서 말한 number, string, boolean 또는 object 유형이 위에서 권장한 소문자 버전과 동일하다고 생각할 수 있으나, 이러한 유형은 언어 primitive를 나타내지 않으며, type으로 사용해서는 안된다.

```ts
function reverse(s: String): String {
  return s.split("").reverse().join("");
}

reverse("hello world");
// 올바르지 않음
```

```ts
function reverse(s: string): string {
  return s.split("").reverse().join("");
}

reverse("hello world");
// 올바름
```

```ts
let isOK: Boolean = true;

let isNotOk: boolean = new Boolean(true);
```
