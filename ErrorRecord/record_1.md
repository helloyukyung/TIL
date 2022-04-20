# 'React' refers to a UMD global, but the current file is a module. Consider adding an import instead.

'''
'React' refers to a UMD global, but the current file is a module. Consider adding an import instead.
'''

함수파일을 따로 만들었을 때 발생한 에러

```tsx
export const hiWord = (hi: boolean) => {
  if (hi) {
    return <div>안녕하세요</div>;
  } else {
    return <div>안녕하지 않아요</div>;
  }
};
```

## 해결 방법

함수의return이 jsx 문법으로 되어 있는데 현재 react가 import 되어있지 않다.

Create React App은 버전 4.1이상에서 즉시 사용 가능한 새로운 JSX 변환을 지원하지만 사용자 정의 설정을 사용하는 경우
`import React from "react"`
다음 import 가 필요하다.

package.json에서 프로젝트의 typescript의 버전을 확인해봤을때 4.1이하였다.

```
 "typescript": "4.0.5"
```
