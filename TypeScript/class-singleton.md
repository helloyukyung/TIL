```ts
export class OnlyOne {
  private static instance: OnlyOne;
  public name: string;

  private constructor(name: string) {
    this.name = name;
  }

  public static getInstance() {
    if (!OnlyOne.instance) {
      OnlyOne.instance = new OnlyOne("싱글톤 객체");
    }
    return OnlyOne.instance;
  }
}

let bad_case = new OnlyOne("오류발생!");

let good_case = OnlyOne.getInstance();
```
