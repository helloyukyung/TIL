for
====

```js
for(초기식; 조건식; 증감식){
    참일때 반복적으로 실행하고자 하는 실행문
}
```

```js
    for (var i = 1; i < 10; i++) {
      document.write(i + "<br>");
    }
```

<h3>document.write()</h3>

script 내에 위 출력문을 넣으면 HTML페이지에 출력

<h3>증감연산자 </h3>

숫자를 1증가 or 1 감소시키고 싶을 때 사용 

- ++는 1증가, --는 1감소
- a++는 더하기 직전의 값, a--는 더한 다음의 값
```
let a = 1;
console.log(a++); //1
console.log(++a); //3
```

<h3>대입연산자</h3>

특정 값에 연산한 값을 바로 사용할 수 있게 함

```js
let a = 2;
a += 1 // a값에 1 더하기 
a -= 1 // a값에 1 빼기 
a *= 1 // 곲하기
a /= 1 // 나누기
console.log(a)
```

<h3>논리연산자</h3>

- ! : not
- && :and 
- || : or 