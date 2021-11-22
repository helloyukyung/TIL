# ResponsiveWebDesign

옛날에는 컴퓨터 화면으로만 웹을 봤다면 이제, 사용자들은 다양한 테블릿 pc와 스마트폰의 등장으로 다양한 size의 화면으로 웹사이트를 이용하게 되었다.

CONTENT IS LIKE WATER  
컨텐츠가 담기는 컨테이너에 따라 유동적으로 바뀌어야 한다.  
-> RESPONSIVE DESIGN

FlUID LAYOUT을 위해서는 px(고정된)보다 Flex grid, Flex box , vh, vw, % 등을 이용해야한다.

## Media Queries

단위를 설정해 Desktop, tablet, mobile 환경에 맞게 웹 환경을 조절할 수 있다.

mobile - 320px ~ 480px  
tablet - 768px ~ 1024px  
desktop - 1024px

```css
@media screen and (min-width: 800px) {
  .container {
    width: 50%;
  }
}
```

최소 넓이가 적어도 800px 일때 아래 스타일링을 하도록 함
