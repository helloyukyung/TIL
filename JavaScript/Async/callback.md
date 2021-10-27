Callback
====
동기와 비동기 
----
javascript는 동기적이다. <br/>
javascript는 호스팅이 된 이후부터 코드 순서에 맞춰 동기적으로 실행된다. (호스팅이란(hosting): var, function  변수, 함수를 선언한 것) 

<h2>Synchronous(동기)</h2>

```js
console.log('1')
console.log('2')
console.log('3')
```
값은 순서대로 1,2,3 동기적으로 실행

<h2>Asynchronous(비동기)</h2>

```js
console.log('1')
setTimeout(function() {
    console.log(2);
    },1000)
console.log('3')
```
값은 1,3 이 찍히고 1초뒤 2가 찍힌다.
setTimeout(browser api,web api)는 브라우저에 api를 요청해 1초뒤 실행 시켜달라고 했기 때문 -> 비동기적으로 동작한 함수 callback 함수

setTimeout안의 함수는 파라미터, 이 함수를 나중에 (1초 뒤에 )전달시켜달라고 하는 것이다.</br> 
따라서 이러한 함수를 callback 함수라고 부른다.</br>
(간단한 arrow function으로 나타낼 수 있다.)

```js
console.log('1')
setTimeout(()=> 
    console.log(2);
    ,1000)
console.log('3')
```


Synchronous callback (동기적인 callback)
----
```js 
function printImmediately(print) {
    print();
}
printImmediately(()=>console.log('hello'))
```
요청과 결과가 동시에 출력된다(동기적).

Asynchronous callback(비동기적인 callback)
----

```js
function printWithDelay(print,timeout) {
    setTimeout(print,timeout);
}
printWithDelay(()=> console.log('async callback'),2000)
```
값이 2초 뒤에 출력된다(비동기적).

콜백지옥
----
 계속해서 안에 콜백을 넣어 복잡하게 만들어진 콜백지옥,,,
 
1. 읽기가 거북함 
2. 비지니스 로직을 알기도 힘듬
3. 에러가 발생했을때 디버깅, 문제분석이 힘듬 
