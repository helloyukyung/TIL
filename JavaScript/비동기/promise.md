Promise
====
JS에서 비동기를 간편하게 처리할 수 있도록 도와주는 Javascript 내장 object
  
비동기적인 기능을 수행할 때 callback 함수보다 더 유용하게 쓸 수 있다.

promise에서는 'state'와  'Producer vs Consumer'에 대해 잘 파악하는 것이 중요하다. 

 State
----
State(상태)를 잘 봐야 한다. </br>
heavy한 동작을 수행 중인지,
 기능수행이 끝난 뒤 성공했는지 실패했는지에 대한 상태를 이해하는 것이 중요하다.

State : pedding(보류 중;operation 수행 중일 때) -> fulfilled or rejected (operation 끝났을 때)


 Producer vs Consumer 
----
데이터를 제공하는부분(Producer)과 쓰는부분(Consumer)을 이해하기

<h3>1. Producer</h3>

새로운 producer 가 생성되면 자동으로 executer 가 실행된다. </br>
Promise는 executer callback(resolve, reject)함수를 전달해줘야한다.</br>
promise를 통해 비동기적으로 heavy한 일들을 한다. </br>
Promise가 만들어지면, 바로 자동으로 executer 함수가 실행된다.</br>
만약, 버튼을 눌렀을 때 네트워크가 실행되길 원했다면 불필요한 네트워크 통신일 수 있다.

```js
const promise = new Promise((resolve,reject)=> {
    // heavy한 일들을 함 (network통신, readfiles 등)
    console.log('doing something...');
    setTimeout(()=> {
        //1. resolve('yukyung')// 성공적으로 네트워크에서 받아온 데이터
        //2. reject(new Error('no network'))
    },2000)
});
```
//resolve() :Promise.then 객체를 반환한다. 

<h3>2. Consumers </h3>

- then :정상적으로 수행될 때
- catch :에러가 발생했을 때 error handling 
- finally :성공 실패와 상관없이 무조건 출력

```js
promise
    .then(value =>{
    console.log(value);//원하는 기능 수행 
                       //1.resolve에서 전달된 'yukyung'이 출력
})
    .catch(error=>{
        console.log(error)// error가 출력 
                        //2. Error: no network
    })
    .finally(()=>{
        console.log('finally')
    })

```

<h3>3. Promise Chaining</h3>
비동기적인 기능들을 .then으로 묶어서 처리 가능 

```js
const fetchNumber = new Promise((resolve,reject)=> {
    setTimeout(()=>resolve(1),1000)
})

fetchNumber
    .then(num =>num*3)
    .then(num =>num*4)
    .then(num =>{
        return new Promise((resolve,reject)=>{
            setTimeout(()=> resolve(num -1),1000);
        })
    })
    .then(num=> console.log(num));
```
2초 뒤에 11 출력

<h3>4. Error Handling</h3>

```js
const getBeer = () => new Promise((resolve,reject)=> {
    setTimeout(()=>resolve('🍺'),1000)
})

const getChicken = beer => new Promise((resolve,reject)=> {
    // setTimeout(()=>resolve(`${beer} +`),1000)
    setTimeout(()=>reject(new Error(`${beer} +🍗`)),1000)

})

const getPerfect = chicken => new Promise((resolve,reject)=>{
    setTimeout(()=>resolve(`${chicken}=>😋`),1000)
})

getBeer() //
.then(getChicken)
.catch(error=>{
    return'🍕'
})
.then(getPerfect)
.then(console.log)
.catch(console.log)
```
맥주와 치킨의 조합 (🍺+🍗=>😋)</br>
맥주를 불러오는 데 에러가 생기면 🍕를 반환해줌 (🍕=>😋)