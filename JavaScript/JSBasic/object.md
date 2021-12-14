# Object

객체(object)
자바스크립트의 기본 타입(data type)은 객체(object)다.  
객체는 이름(name)과 값(value)으로 구성된 프로퍼티(property)의 정렬되지 않은 집합을 의미한다.
프로퍼티의 값으로 함수가 올 수도 있는데 이 프로퍼티는 메소드(method)라고 한다.

강아지라는 '객체'가 있을 때

프로퍼티(property)

- dog.name = "감자"
- dog.family = "요크셔 테리어"
- dog.age = 7

메소드(method)

- dog.bite()
- dog.eat()
- dog.walk()

```js
var person = {
  name: "김유경", // 이름 프로퍼티를 정의
  birthday: "000107", // 생년월일 프로퍼티를 정의
  pId: "1234567", // 개인 id 프로퍼티를 정의
  fullId: function () {
    // 생년월일과 개인 id를 합쳐서 주민등록번호를 반환
    return this.birthday + this.pId;
  },
};

person.name; // 김유경
person["name"]; // 김유경

person.fullId(); // 0001071234567
person.fullId; // function () { return this.birthday + this.pId; }
```
