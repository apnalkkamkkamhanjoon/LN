# 모듈로 만들기

> 노드는 코드를 모듈로 만들 수 있다는 점에서 브라우저의 자바스크립트와는 다르다. _모듈_ 은특정한 기능을 하는 함수나 변수들의 집합이다.

## 장점

> 모듈로 만들어두면 여러 프로그램에 해당 모듈을 재사용할 수 있다. 자바스크립트에서 코드를 재사용하기 위해 함수로 만드는 것과 비슷하다. 파일별로 코드를 모듈화할 수 있어 관리하기 편하다.

## 모듈 사용하기

> 모듈을 만들 때 모듈이 될 파일과 모듈을 불러와서 사용할 파일이 필요하다.

var.js

```js
const odd = "홀수";
const even = "짝수";

module.exports = {
  odd,
  even,
};
```

func.js

```js
const { odd, even } = require("./var");

function checkOddOrEvne(num) {
  if (num % 2) {
    return odd;
  }
  return even;
}

module.exports = checkOddOrEven;
```

`require`함수 안에 불러올 모듈의 경로를 적어준다. `require`함수의 인자로 제공하는 경로만 잘 지정하면 된다. 파일 경로에서 js나 json 같은 확장자는 생략할 수 있다.

index.js

```js
const { odd, even } = require("./var");
const checkNumber = require("./func");

function checkStringOddOrEven(str) {
  if (str.length % 2) {
    return odd;
  }
  return even;
}
console.log(checkNumber(10));
console.log(checkStringOddEven("hello"));
```

모듈로 값을 불러올 때 변수 이름을 다르게 지정할 수도 있다. `func.js`의 `checkOddOrEven`이 `checkNumber`라는 이름으로 사용되고 있다.

콘솔

```bash
& node index
짝수입니다
홀수입니다
```
