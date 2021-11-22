#Classes
class는 객체를 생성하기 위한 탬플릿.

Class는 "특별한 함수"다. class 문법은 class 표현식 and class 선언 두 가지 방법을 사용할 수 있다.

```js
//class 표현식
const Rectangle = class {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
  area() {
    return this.height * this.width;
  }
};

console.log(new Rectangle(5, 8).area());
//output: 40

//class 선언
class Polygon {
  constructor(height, width) {
    this.area = height * width;
  }
}

console.log(new Polygon(4, 3).area);
```

class 선언 : 클래스의 이름(Rectangle)과함께 class 키워드 사용
class 를 사용하기 위해너는 클래스를 먼저 선언해야 한다.
