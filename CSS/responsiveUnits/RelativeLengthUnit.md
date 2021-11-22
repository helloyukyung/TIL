# Relative length units

em, ex, ch, rem, v\*, % 등 다양한 relative units이 존재한다.

## em

typograpy에서 현재 지정된 point 사이즈를 나타낸다(폰트사이즈를 나타내는 단위).  
같은 font size를 가지고 있다고 할지라도, font family에 따라 사용자에게 보여지는 크기가 다를 수 있다.  
em은 선택된 font-family에 상관없이 고정된 font-size를 유지한다.

- 1em ==16px

```html
<div class="parent">
  Parent
  <div class="child">Child</div>
</div>
```

```css
.parent {
  font-size: 8em; //==800%
}
.child {
  font-size: 0.5em; //==50%
}
```

부모의 font-size에 맞게 값이 상대적으로 조절된다.  
부모: 16(기본값)px *8 = 128 px  
자식:128px *0.5 = 64 px

## ex, ch

ex는 em 과 달리 지정된 font-faimily의 크기에 따라 높이가 변경될 수 있다.
ch는 적용된 font-family에서 0의 너비를 나타내는 단위

## rem

root + em

부모에 따라 값이 지정되는 em과는 달리 rem은 root에 지정된 font-size에 따라 값이 지정된다.

```html
<div class="parent">
  Parent
  <div class="child">Child</div>
</div>
```

```css
.parent {
  font-size: 8rem;
}
.child {
  font-size: 0.5rem;
}
```

부모: 16(기본값)px *8 = 128px  
자식:16 (기본값)px *0.5 = 8px

## vw, vh, vmin, vmax

viewport에 따라 값을 지정
vw : viewport width
vh : viewport height

## %

parent related 부모요소에 따라 값이 상대적으로 계산된다.
