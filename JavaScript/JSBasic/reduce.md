# reduce

반복되는 모든 것에는 reduce를 쓸 수 있다.<br/>
reduce로 map과 filter와 같은 함수형 메소드가 구현이 가능하다.

## reduve method

```js
배열.reduce((누적값, 현잿값, 인덱스) => {
  return 결과;
}, 초깃값);
```

```js
const array = [3, 1, 10, 2, 5];
const sum = array.reduce(function (accumulator, currentValue, index) {
  // console.log(accumulator, index);
  // console.log(currentValue);
  return accumulator + currentValue;
}, 0);
console.log(sum);

// console.log(sum)
// 21

// console.log(accumulator, index)
// 3 0
// 4 1
// 14 2
// 16 3

// console.log(currentValue)
// 1
// 10
// 2
// 5
```

## reduce로 map함수 구현

```js
oneTwoThree = [1, 2, 3];

result = oneTwoThree.reduce((acc, cur) => {
  acc.push(cur % 2 ? "홀수" : "짝수");
  return acc;
}, []);
result;
// ['홀수', '짝수', '홀수']
```

## reduce로 filter함수 구현

```js
result = oneTwoThree.reduce((acc, cur) => {
  if (cur % 2) acc.push(cur);
  return acc;
}, []);
result;
// [1, 3]
```
