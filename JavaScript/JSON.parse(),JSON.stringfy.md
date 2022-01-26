# JSON.parse() & JSON.stringify()

## JSON.parse()

JSON.parse()는 string객체를 json객체로 변환 시켜준다 .

```js
console.log(localStorage.getItem("marks"));
//[{"contents":"test1","spelling":"add","category":"v","meaning":"더하다","remember":false,"wrong_count":1,"account":84},{"contents":"test1","spelling":"world","category":"n","meaning":"세상","remember":false,"wrong_count":2,"account":84}]

console.log(JSON.parse(localStorage.getItem("marks")));
//(2) [{…}, {…}]
// 0: {contents: 'test1', spelling: 'add', category: 'v', meaning: '더하다', …}
// 1: {contents: 'test1', spelling: 'world', category: 'n', meaning: '세상', …}
// length: 2
// [[Prototype]]: Array(0)
```

## JSON.stringify()

JSON.stringify는 JavaScript 객체를 JSON 문자열로 반환한다.

```js
JSON.stringify(value, replacer, space);
```

- value(필수): JSON 문자열로 변환할 값이다.(배열, 객체, 또는 숫자, 문자 등이 될 수 있다.)

- replacer(선택): 함수 또는 배열이 될 수 있다. 이 값이 null 이거나 제공되지 않으면, 객체의 모든 속성들이 JSON 문자열 결과에 포함된다.

- space(선택): 가독성을 목적으로 JSON 문자열 출력에 공백을 삽입하는 데 사용된다.

```js
let word = { spelling: "hello", meaning: "안녕하세요" };

object_as_string = JSON.stringify(word);

// '{"spelling":"hello","meaning":"안녕하세요"}'
typeof object_as_string;
// 'string'
```
