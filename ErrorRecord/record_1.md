# 'React' refers to a UMD global, but the current file is a module. Consider adding an import instead.

'''
'React' refers to a UMD global, but the current file is a module. Consider adding an import instead.
'''

함수파일을 따로 만들었을 때 발생한 에러

```tsx
export const hiWord = (hi: boolean) => {
  if (hi) {
    return "안녕하세요";
  } else {
    return "안녕하지 않습니다.";
  }
};
```

## 해결 방법

Create React App은 버전 4.1이상에서 즉시 사용 가능한 새로운 JSX 변환을 지원하지만 사용자 정의 설정을 사용하는 경우
`import React from "react"`
다음 import 가 필요하다.

package.json에서 프로젝트의 typescript의 버전을 확인해봤을때 4.1이하였다.

```
 "typescript": "4.0.5"
```
