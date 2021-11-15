# map()

map() 함수는 반복문을 돌며 배열을 받아와 원하는 배열을 반환한다.

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

markers뒤에 ?.(optionalChaining) 을 붙여 markers내에 빈 값이 있어도 map() 함수가 실행되게끔 해주었다.

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
