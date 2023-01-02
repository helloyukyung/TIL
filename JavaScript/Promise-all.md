# Promise.all 

```js

const handleSubmit = async(values) => {
    const {images, ...rest} = values
    let imageList = []
    for (let i = 0; i < images.length; i++) {
        const currentImageUrl = await uploadFile({file: images[i], type: 'file'})
        if (currentImageUrl) imageList.push(currentImageUrl)
    }
    // ...
}
```

to

```js

const handleSubmit = async(values) => {
    const {images, ...rest} = values
    const imageList = await Promise.all(
        images.map(
            (file) =>
                file &&
                uploadFile({
                    file: file,
                    type: 'file'
                })
        )
    )
    // ...
}
```

`Promise.all(promise)`
모든 프라미스가 이행될 때까지 기다렸다가 그 결괏값을 담을 배열을 반환한다.

주어진 프로미스 중 하나라도 실패하면 Promise.all는 거부되고 나머지 프라미스의 결과는 무시된다. 
