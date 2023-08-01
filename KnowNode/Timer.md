# Timer

> `setTimeout`, `setInterval`, `setImmediate`는 노드에서 `window`대신 `global` 객체 안에 들어있다.

- setTimeout(콜백 함수, 밀리초) : 주어진 밀리초(1000분의 1초) 이후에 콜백 함수를 실행한다.
- setInterval(콜백 함수, 밀리초) : 주어진 밀리초마다 콜백 함수를 반복 실행한다.
- setImmediate(콜백 함수) : 콜백 함수를 즉시 실행한다.

이 타이머 함수들은 모두 아이디를 반환한다. 아이디를 사용하여 타이머를 취소할 수 있다.

- claerTimeout(아이디) : `setTimeout`을 취소한다.
- clearInterval(아이디) : `setInterval`을 취소한다.
- clearImmediate(아이디) : `setImmediate`를 취소한다.

## 예제

timer.js

```js
const timeout = setTimeout(() => {
  console.log("1.5초 후 실행");
}, 1500);

const interval = setInterval(() => {
  console.log("1초마다 실행");
}, 1000);

const timeout2 = setTimeout(() => {
  console.log("실행되지 않습니다");
}, 3000);

setTimeout(() => {
  clearTimeout(timeout2);
  clearInterval(interval);
}, 2500);

const immediate = setImmediate(() => {
  console.log("즉시 실행");
});

const immediate2 = setImmediate(() => {
  console.log("실행되지 않습니다.");
});

clearImmediate(immediate2);
```

제일 먼저 실행되는 것은 `immediate`이다. `immediate2`는 바로 `clearImmediate`를 사용하여 취소했기 떄문에 실행되지 않는다. 코드 실행 1초 후에는 `interval`의 콜백이 실행된다. 코드 실행 1.5초 후에는 `timeout`의 콜백이 실행될 것이다. `interval`의 콜백은 1초마다 실행되어 코드 실행 후 2초가 지났을 때에도 콜백이 실행된다. 2.5초가 지났을 때 `clearTimeout`과 `clearInterval`이 각각 `timeout2`와 `interval`을 취소한다. 따라서 코드 실행 3초 후에는 로그가 아무것도 남지 않는다.

## 콘솔

```bash
$ node timer
즉시 실행
1초마다 실행
1.5초 후 실행
1초마다 실행
```
