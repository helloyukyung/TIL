# Size Unit (em / ex / px / pt / %)

CSS는 단위(길이)를 표현하기 위한 여러가지 단위가 있으며, width, margin, padding, font-size, border-width 등과 같은 많은 CSS 속성에서 사용된다.

## 절대단위&상대단위

CSS에는 절대 길이 단위(Absolute length units)와 상대 길이 단위(Relative length units)개념이 있다.

반응형 웹에서 폰트를 px같은 절대 길이 단위로 지정하면 컨테이너 사이즈를 조정해도 폰트 크기가 고정값으로 유지되어 변하지 않는다.<br/>
또한, 사용자가 브라우저 내 설정에서 폰트 사이즈를 변경해도 적용되지 않는다.

반대로, 브라우저를 기준으로 폰트사이즈를 유연하게 쓰고 싶다면 %와 같은 상대길이단위로 폰트를 설정해줘야 한다.

절대길이에는 보통 px, pt를 많이 쓰며,
상대길이에는 em, rem, vw, vh, % 등이 있다.

## 상대단위 종류

### em

1em =16px 이다.<br/>
그러다 상대단위인 이유는 부모요소를 기준으로 자식요소의 폰트사이즈가 정해지기 때문이다.<br/>

```
.parent {
	font-size: 4em;	/* px로 변환하면 4 * 16 = 64px */
}
.child {
	font-size: 1em;	/* parent요소의 1배 크기 = 64px */
}
```

### vw & vh

웹에서 viewport는 화면에서 보이는 부분을 말한다.<br/>
vw & vh는 현재 실행중인 스크린 크기에 맞춰 상대적 크기를 반환한다.<br/>
vw는 viewport width, vh는 viewport height를 의미하며, 100vh, 100vw 가 전체 화면의 기준이 된다. <br/>

(ex. 50vw는 전체 화면 너비의 50%,
10vh는 전체 화면 높이의 10%)
