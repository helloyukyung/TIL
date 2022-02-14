# "=="vs"==="

==는 Equal Operator이고, ===는 Strict Equal Operator이다.
===는 "엄격하게" 같음을 비교할 때 사용하는 연산자이다.

```js
var a = 1;
var b = "1";
console.log(a == b); // true
console.log(a === b); // false
```

숫자 1과 문자열 1의 경우 == 는 true 지만 === 는 false

```js
console.log(null == undefined); // true
console.log(null === undefined); // false
```

이외에도 null과 undefined는 둘 다 값이 없음을 표시하지만, 데이터 타입이 다르므로 강한 검사에서는 false가 출력된다.
