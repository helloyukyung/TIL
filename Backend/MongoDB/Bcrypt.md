# Bcrypt

Bcrypt를 사용해 비밀번호를 암호화하여 데이터베이스에 저장해줘야 한다.

```json
{
  "email": "email@naver.com",
  "password": "1234567"
}
```

1. saltrounds(비밀번호자리수)생성
2. salt 생성
3. salt로 암호화

```js
userSchema.pre("save", function (next) {
  var user = this;

  if (user.isModified("password")) {
    bcrypt.genSalt(saltRounds, function (err, salt) {
      if (err) return next(err);
      bcrypt.hash(user.password, salt, function (err, hash) {
        if (err) return next(err);
        user.password = hash;
        next();
      });
    });
  } else {
    next();
  }
});
```

모델 field 에서 password가 변환될때만 bcrypt를 이용해 암호화

```json
{
    email:"email@naver.com",
    password: "$2b$10$p.5qVDBwDzXeU4qJjFE.m.17tHFwAyq0W6M5ae8Se.L9mIdWoWeJm";
}
```
