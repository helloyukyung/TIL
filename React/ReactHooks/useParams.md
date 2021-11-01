useParams
====
중복을 방지해주는 훅중 하나 
주소를 라우팅해준다. 
useParams를 통해 원하는 값과 라우터를 매치해줌( path parameter의 정보를 제공해줌).

```jsx
//in LoginRouter.jsx
 <Route path="/day/:day"> 
    <Day/>
</Route>
```

```jsx
//in Day.jsx
const { day } = useParams();
const wordList = dummy.words.filter(word=> word.day === Number(day))

```
- 앞에 'LoginRouter'컴포넌트에서 path 뒤에 ':day'는 day값에 따라 주소가 달라짐. 
- 그리고 'Day'컴포넌트에서 useParams를 통해path parameter(동적 라우팅값)를 읽어옴.