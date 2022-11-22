## useScript 

```ts
import {useEffect} from 'react'

const useScript = (url: string) => {
  useEffect(() => {
    const script = document.createElement('script')
    script.src = url
    script.async = true

    document.body.appendChild(script)

    return () => {
      document.body.removeChild(script)
    }
  }, [url])
}

export default useScript

```

여러페이지를 쓰이는 곳이 아닌 스크립트의 경우 (ex. 로그인,맵) useScript를 사용해 사용할 컴퍼넌트에서 
스크립트를 불러올 수 있도록 했다. 

하지만 네이버 로그인의 경우, <div id='naverIdLogin' />을 넣어 조작 하는데,
이 때문에 페이지(view)가 그려지고 스크립트(useEffect)가 불려져 
스크립트가 불려지기 전에 id를 건들여 해당 훅을 사용할 수가 없었다.(뇌피셜)

```
Uncaught TypeError: Cannot read properties of undefined (reading 'LoginWithNaverId')


React Router caught the following error during render TypeError: Cannot read properties of undefined (reading 'LoginWithNaverId')
```

잘 쓸 수 있을거라 생각해 적용했는데, 잘 쓰지 못한,,