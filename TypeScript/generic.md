# Generic

제너릭 타입은 타입에 유연성을 제공하여 컴포넌트 등에서 재사용을 가능하게 해주는 타입을 의미한다.

타입의 유연성이란 :string , :number 등과 같이 고정된 타입이 아닌 사용에 따라 여러 타입을 사용하게 해주는 것을 의미한다.

이는 :any 와 같다고 생각할 수 있지만, 타입의 정보가 동적으로 결정된다는 차이가 있다.  
(아래 예시 참고)

## any 타입 사용 코드

```tsx
// identity의 인자 타입 :any
// identity함수가 반환하는 타입 :any
function identitiy(arg: any): any {
  return arg;
}

const example = identitiy(1);

console.log(example);
example.split(``);
// code 상에서 빨간줄(에러)가 발생하지 않음
```

identity는 any타입으로 인자를 받아 그 인자를 any로 반환하는 함수다.

identity(1)을 example변수에 할당했을 때, example값의 타입은 any이므로 문자열메서드인 split()을 사용할 수 있는 오류가 발생한다.

```tsx
// identity의 인자 타입 :any
// identity함수가 반환하는 타입 :number
function identitiy(arg: any): number {
  return arg;
}

const example = identitiy(1);

console.log(example);
example.split(``);
// code 상에서 빨간줄(에러)가 발생 (good)
```

identity 반환값을 number로 설정하면 , 문자열 메소드 사용에 빨간줄(에러)이 난다.

## generic 사용 코드

```tsx
// identity의 인자 타입 : <T>
// identity함수가 반환하는 타입 :<T>
function identitiy<T>(arg: T): T {
  return arg;
}

const example = identitiy(1);

console.log(example);

example.split(``);
// code 상에서 빨간줄(에러)가 발생 (good)
```

이 결과 숫자 1을 넣으면 그 인자의 타입이 T로 설정된다.
따라서 idnetity함수가 반환하는 타입은 number가 되고, 문자열 메소드인 split() 사용에 오류를 감지할 수 있다.

```tsx
function identitiy<T>(arg: T): T {
  return arg;
}

const example = identitiy("hi");

console.log(example);

example.split(``);
```

만약 인자 값에 "hi"(문자열)을 넣어주면
idnetity함수가 반환하는 타입은 string이므로.
문자열 메소드인 split()를 사용할 수 있다.

따라서 generic을 사용했을 때 타입정보가 동적으로 결정된다는 것을 알 수 있다.
