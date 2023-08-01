# module, exports

> 모듈을 만들 때 `module.exports`만 사용했다. `module` 객체 말고 `exports` 객체로도 모듈을 만들 수 있다.

## 예제

var.js

```js
exports.odd = "홀수입니다";
exports.even = "짝수입니다";
```

## 콘솔

```bash
$ node index
짝수입니다.
홀수입니다.
```

`module.exports`로 한 번에 대입하는 대신, 각각의 변수를 `exports` 객체에 하나씩 넣었다. 동일하게 동작하는 이유는 `module.exports`와 `exports`가 같은 객체를 참조하기 때문이다.
