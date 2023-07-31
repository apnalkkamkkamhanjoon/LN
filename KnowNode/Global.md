# global

> 브라우저의 `window`와 같은 전역 객체다. 전역 객체이므로 모든 파일에서 접근할 수 있다. 또한 `window.open` 메서드를 그냥 `open`으로 호출할 수 있는 것처럼 `global`도 생략할 수 있다.

## 예제

globalA.js

```js
module.exports = () => global.message;
```

globalB.js

```js
const A = require("./globalA");

global.message = "안녕하세요";
console.log(A());
```

`$node globalB`

> 안녕하세요
