async & await
====
async/await은 promise를 좀 더 편리한 API를 제공하는것. (syntactic sugar)

<h3>1. async</h3>

이전 promise로 만들었던 코드를 async로 고쳐보자.

before 
```js
function fetchUser() {
    return new Promise((resolve,reject)=>{
        //do network request in 10 secs...
        resolve('🙂');
    });
}

const user = fetchUser();
console.log(user)

```
after

```js
async function fetchUser() {
    return '😁'
}

const user = fetchUser();
user.then(console.log)
// console.log(user)


```


<h3>2. await</h3>
await은 async가 붙은 함수 안에서만 쓸 수 있다.

```js

function delay(ms) {
    //정한 ms가 지나면 resolve를 호출하는 함수
    return new Promise(resolve => setTimeout(resolve,ms));
}

async function getApple() {
    await delay(1000);
    throw 'error'
    return 'apple'
}
async function getBanana() {
    await delay(1000);//delay가 끝날 때까지 기다려줌
    return 'banana'
}

//promise로 getBanana를 썼을 때
// function getBanana() {
//     return delay(3000)
//     .then(()=> 'banana')
// }
// 

async function pickFruits() {
    const applePromise = getApple();
    const bananaPromise = getBanana();
    const apple = await applePromise();
    const banana = await bananaPromise();

    return `${apple} + ${banana}`;
}

pickFruits().then(console.log)
```
promise로 표현했을 때, 보다 더 '동기적'으로 보기 쉽다. 

3.<h3> await 병렬처리 </h3>

apple과 banana는 독자적이므로 서로를 기다릴 필요가 없음.</br>
pickFruits()함수에서
 `const apple = await getApple()`뒤에 `const banana = await getBanana()`을 추가하면 apple-delay1초(1000)를 기다리고 또 Banana-delay(1000)1초를 기다려야 한다(runnung time: 2sec/직렬).</br>
 그러므로 promise 함수를 만들어 호출시켜놓고 불러오자(running time: 1sec/병렬).






