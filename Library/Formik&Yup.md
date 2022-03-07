# Formik & Yup

`Formik`은 동기 및 비동기 양식 수준 및 필드 수준 유효성 검사를 지원하며,

`Yup`을 통해 스키마 기반 양식 수준 유효성 검사를 수행할 수 있다.

즉 많은 input값을 작성할 때, 우리는 일일이 해당 input값에 대한 useState와 handleChange를 작성해야 될 것이다.

이렇게 되면 코드의 양은 증가할 것이고 더러워 질것이다. 이런 귀찮은 작업을 Formik 라이브러리로 해결할 수 있다.

다음 코드를 통해 Formik & Yup에 대해 알아보자

```js
// src/components/signup.js
import React from "react";
import "./Signup.css";
import { useFormik } from "formik";
import * as Yup from "yup";

export default function Signup() {
  const formik = useFormik({
    initialValues: {
      firstName: "",
      lastName: "",
      email: "",
    },
    validationSchema: Yup.object({
      firstName: Yup.string()
        .max(15, "must be 15 characters or less")
        .required("Required"),
      lastName: Yup.string()
        .max(20, "must be 20 characters or less")
        .required("Required"),
      email: Yup.string().email("Invalid email address").required("Required"),
    }),
    onSubmit: (values) => {
      console.log(values);
    },
  });

  return (
    <form onSubmit={formik.handleSubmit}>
      <div className="input-container">
        <input
          id="firstName"
          name="firstName"
          type="text"
          placeholder="First Name"
          onChange={formik.handleChange}
          onBlur={formik.handleBlur}
          value={formik.values.firstName}
        />
        {formik.touched.firstName && formik.errors.firstName ? (
          <p>{formik.errors.firstName}</p>
        ) : null}
        <input
          id="lastName"
          name="lastName"
          type="text"
          placeholder="LastName"
          onChange={formik.handleChange}
          onBlur={formik.handleBlur}
          value={formik.values.lastName}
        />
        {formik.touched.lastName && formik.errors.lastName ? (
          <p>{formik.errors.lastName}</p>
        ) : null}
        <input
          id="email"
          name="email"
          type="text"
          placeholder="Email"
          onChange={formik.handleChange}
          onBlur={formik.handleBlur}
          value={formik.values.email}
        />
        {formik.touched.email && formik.errors.email ? (
          <p>{formik.errors.email}</p>
        ) : null}
      </div>
      <button type="submit">submit</button>
    </form>
  );
}
```

![](https://images.velog.io/images/yukyung123/post/c2919dc8-ad4c-45c7-9d4f-5fd97053f589/image.png)
먼저 `initialValues`는 input값들의 초기값을 의미한다.

```js
onChange={formik.handleChange}
value={formik.values.firstName}
```

위와같이 useState대신 formik을 사용해 state값을 조정할 수 있다.

```js
onBlur={formik.handleBlur} // 해당 input값을 클릭한 뒤 다른 곳을 클릭하면 true
```

`formik.handleBlur`는 해당 input이 클릭되었을 때 touched가 true로 변경된다.
이를 통해 해당 `input`이 click 된 이후 해당 값을 채우지 못했을 때, error 메세지("Required")를 뱉어내게 할 수 있다.

```js
{
  formik.touched.firstName && formik.errors.firstName ? (
    <p>{formik.errors.firstName}</p>
  ) : null;
}
```

위와 같이 firstName값이 한번 클릭 된 이후(touched) 그리고 해당 값이 error에 해당할 때, `<p>{formik.errors.firstName}</p>`메세지를 출력한다.
![](https://images.velog.io/images/yukyung123/post/8f6a4df1-9d2d-4903-9b3c-2f1b2c4b4dc7/image.png)
