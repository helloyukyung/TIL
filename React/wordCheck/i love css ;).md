flexbox froggy remind
====
먼저 flex box를 만들어줌
```
.flex_container {
    display:flex;
}

```
flex 속성이 적용된 요소는 flex container.

 flex container의 자식(자식요소)은 flex item.

 부모 요소와 자식 요소에 정의하는 속성 구분
----

- flex container 속성: flex-direction, flex-wrap, justify-content, align-items, align-content

- flex item 속성: flex, flex-grow, flex-shrink, flex-basis, order

<br>
<br>

-----


<h3> ex. justify-content</h3>

- flex-start: 요소들을 컨테이너의 왼쪽으로 정렬
- flex-end: 요소들을 컨테이너의 오른쪽으로 정렬
- center: 요소들을 컨테이너의 가운데로 정렬
- space-between: 요소들 사이에 동일한 간격을 둠
- space-around: 요소들 주위에 동일한 간격을 둠 

```
#pond {
  display: flex;
justify-content: center;
}
```