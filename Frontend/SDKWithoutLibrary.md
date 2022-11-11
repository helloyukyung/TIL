# SDK Without Library

이전에는 라이브러리로만 썼었는데, 그냥 script 추가해주고 
인스턴스만 생성해주면 끝났다.

아무것도 모르고 라이브러리만 설치했던 것에 반성하자

```html
// html 파일에 script 추가 
<script src="//t1.daumcdn.net/mapjsapi/bundle/postcode/prod/postcode.v2.js"></script>
```

```tsx

const  index = () => {
    return
    (<button onClick={()=>{new window.daum.postCode({onComplete : (data : any) => {console.log(data)}}).open()} } >주소 불러오기</button>
)
} 

```
react 스럽게
```tsx
const index = () => {
    
    const daum = useRef()
    
    useEffect (() =>{
        if (window.daum){
            daum.current = new window.daum.Postcode({})
        }
    },[])
    
    return
    (<button  onClick={()=>daum.current.open()} >주소 불러오기</button>
)
} 



```