# Model & Schema

## Schema
MongoDB와 같은 nosql은 테이블이 없어서 아무거나 넣을 수 있다. 이 때문에 문제가 생기는데 몽구스는 이러한 문제를 막기 위해서 Schema(스키마)를 도입했다.

```js
const mongoose = require('mongoose');

const userSchema = new mongoose.Schema({
  writer: {
    type: Schema.Types.ObjectId,
    ref: 'User'
  },
  title: {
    type: String,
    maxlength: 50
  },
  description: {
    type: String
  }
});
```

title 필드의 자료형은 문자열이고, 최대 길이가 50이어야 한다.  
위와 같이 하나하나 지정을 해주는 것을 스키마라고 한다.

## Model
Model은 Schema(스키마)를 감싸주는 것이다. 위의 코드의 하단 부분에 다음과 같은 코드를 입력한다.

```js
const User = mongoose.model('User', userSchema);

module.exports = { User };
```

이러면 userSchema라는 스키마를 감싸는 User라는 모델이 만들어지고 이를 exports 하면 외부 소스에서 불러올 수 있다.