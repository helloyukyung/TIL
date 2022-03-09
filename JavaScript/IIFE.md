# IIFE

IIFE(Immediately Invoked Function Expression), 즉시 실행함수 표현은 정의되자마자 즉시 실행되는 자바스크립트 function을 말한다.

```
(function () {
    statements
})();
```

두부분으로 나눌 수 있는데 첫번째는 괄호로 둘러싸인 익명함수다.  
이는 전역 스코프에 불필요한 변수를 추가해서 오염시키는 것을 방지할 수 있을 뿐 아니라 IIFE 내부안으로 다른 변수들이 접근하는 것을 막을 수 있다.

두 번째 부분은 즉시 실행 함수를 생성하는 괄호()이다. 이를 통해 자바스크립트 엔진은 함수를 즉시 해석해서 실행한다.

```js
(function () {
  var name = "Sally";
  return name;
})();
//'Sally'
```
