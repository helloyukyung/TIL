# table

table은 표를 만드는 태그를 말한다.  
table 태그안에 th, tr, td tag를 넣어준다.

## th,tr,td

th는 header cell, 표의 제목을 의미  
tr은 table row, 가로줄을 의미  
td는 table data, 셀을 만드는 역할

### gachiGaGae에서 구현한 CoffeeMenu table 표

```jsx
(
  <table>
    <tr>
      <th>Coffee</th>
      <th>Price</th>
    </tr>
    {detail.menu.map((menu) => (
      <tr className="Menuinfo">
        {menu.category === "coffee" ? (
          <td>
            {menu.name}
            {!!menu.is_main && <MenuBadge color="#ff9966">메인메뉴</MenuBadge>}
            {!!menu.is_popular && (
              <MenuBadge color="#ffe680">인기메뉴</MenuBadge>
            )}
          </td>
        ) : null}
        {menu.category === "coffee" ? <td> {menu.price}</td> : null}
      </tr>
    ))}
  </table>
)``;
```
