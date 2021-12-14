# Model$Schema

스키마는 해당 컬렉션의 문서에 어떤 종류의 값이 들어가는지를 정의힌다.

모델은 스키마를 통해서 만드는 인스턴스, 스키마를 감싸주는 역할을 한다.

웹사이트의 회원가입 부분에서 유저이름이나 나이 등을 입력해야한다고 할때,유저와 관련된 데이터들을 보관하기 위해 usermodel, userschema를 만들어줘야 한다.

## productschema & productmodel

```js
const mongoose = require('mongoose');
const Schema = mongoose.Schema;

const productSchema = mongoose.Schema({
    writer:{
        type : Schema.Types.ObjectId,
        ref:'User'
    },
    title :{
        type:String,
        maxlength:50
    },
    description: {
        type::String
    }
},{timestamps:true})

const Product = mongoose.model('Product',productSchema);

module.exports = Product
```
