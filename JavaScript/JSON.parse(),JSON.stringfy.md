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

JSON.stringify는 JavaScript 객체를 JSON 텍스트로 바꾸고 해당 JSON 텍스트를 문자열에 저장해준다.

```js
let word = { spelling: "hello", meaning: "안녕하세요" };

object_as_string = JSON.stringify(word);

// '{"spelling":"hello","meaning":"안녕하세요"}'
typeof object_as_string;
// 'string'
```
