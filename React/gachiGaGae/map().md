# map()

map() 함수는 반복문을 돌며 배열을 받아와 원하는배열을 반환한다.

## 에러코드

```jsx
{
  markers.map((marker) => (
    <Marker
      key={marker.shop_id}
      position={new navermaps.LatLng(marker.latitude, marker.longitude)}
      animation={0}
      onClick={() => {
        alert(`여기는 ${marker.name}`);
      }}
    />
  ));
}
```

API로 받아온 Data에 Marker를 찍기위해 다음과 같이 map함수를 작성하여 실행시켰으나 아래 error 발생

```
TypeError: Cannot read properties of null (reading 'map')
```

구글링 결과 `markers`가 빈값을 받아온 것 같다.

marker뒤에 ? 을 붙여 Marker가 있으면 map() 함수가 실행되게 해주었다.

## 해결코드

```jsx
{
  markers?.map((marker) => (
    <Marker
      key={marker.id}
      position={new navermaps.LatLng(marker.latitude, marker.longitude)}
      animation={0}
      onClick={() => {
        alert(`여기는 ${marker.name}`);
      }}
    />
  ));
}
```
