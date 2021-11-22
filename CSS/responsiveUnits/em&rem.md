# relative units

relative units 중 언제 어떤 unit을 사용하면 좋을지 정리

## 1. parent

부모요소의 사이즈에따라 변경이 되어야한다면
%, em

부모요소와 상관없이 browser에 유동적이고 싶다면 v\* or rem

## 2. box

요소의 너비와 높이에 따라 사이즈가 변경이 되어야한다면 %, v\*

font size에 따라 사이즈가 변경이 되어야한다면 em, rem

px to em 변환 사이트  
http://pxtoem.com/

# em & rem

좋아요 component👍를 만들었다고 해보자.

#em  
상위에서 쓴 좋아요👍(ex.기본값px*10em)와
부모요소안에 쓴 좋아요👍(ex.부모px*10em)는 크기가 다르다.

=> 부모요소에 따라 사이즈가 유동적으로 조절되었으면 좋겠을 때 사용한다.

#rem  
상위에서 쓴 좋아요👍(ex.기본값px*10em)와 부모 요소안의 좋아요👍(ex.기본값(root)px*10em)는 크기가 같다.

=> 페이지 어디에서 쓰더라도 사이즈가 같았으면 좋겠을 때 사용한다.

무조건 정해진 기준이 있는게 아니다. 상황에 따라 유동적으로 사용할 줄 알아야한다.

## em & rem 혼합

```css
.title {
    padding :0.5em 0.5rem;
    background-color: burlywood;
}
.contents {
    font-size :1rem
    padding :0.5em 0.5rem;
}

```

`padding: 0.5em`일 경우, 기존 content에 적용된 font-size의 0.5배가 되어 계산된다.  
하지만, 요소마다 사이즈가 다 다르게 나오게 될것이다(title 과 contents의 수직정렬이 맞지 않음).  
따라서 위 코드와 같이 `padding :0.5em 0.5rem;`고정적인 padding을 유지하고 싶을 경우 위 아래는 값이 조절되도록 em을 준뒤 양옆은 rem을 줘 수직정렬이 될 수 있도록 만들어 줄 수 있다.
