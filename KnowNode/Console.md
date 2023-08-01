## console

> console도 노드에서는 `window` 대신 `global` 객체 안에 들어있다.
> 브라우저에서의 `console`과 비슷하다. `console`객체는 보통 디버깅을 위해 사용된다.

## 예제

console.js

```js
const string = "abc";
const number = 1;
const boolean = true;
const obj = {
  outside: {
    inside: {
      key: "value",
    },
  },
};
console.time("전체 시간");
console.log("평범한 로그입니다 쉼표로 구분해 여러 값을 찍을 수 있습니다");
console.log(string, number, boolean);
console.error("에러 메세지는 console.error에 담아주세요");

console.dir(obj, { colors: false, depth: 2 });
console.dir(obj, { colors: true, depth: 1 });

console.time("시간 측정");
for (let i = 0; i < 100000; i++) {
  continue;
}
console.timeEnd("시간 측정");

function b() {
  console.trace("에러 위치 추적");
}
function a() {
  b();
}
a();

console.timeEnd("전체 시간");
```

- console.time(레이블) : `console.timeEnd(레이블)`과 대응되어 같은 레이블을 가진 `time`과 `timeEnd`사이의 시간을 측정한다.
- console.log(내용) : 평범한 로그를 콘솔에 표시한다. `console.log(내용, 내용)`처럼 여러 내용을 동시에 표시할 수도 있다.
- console.error(에러내용) : 에러를 콘솔에 표시한다.
- console.dir(객체, 옵션) : 객체를 콘솔에 표시할때 사용한다. 첫 번째 인자로 표시할 객체를 넣고, 두번째 인자로 옵션을 넣는다. 옵션의 `colors`를 `true`로 하면 콘솔에 색이 추가되어 보기가 한결 편해진다. `depth`는 객체 안의 객체를 몇 단계까지 보여줄지를 결정한다. 기본값은 `2`이다.
- console.trace(레이블) : 에러가 어디서 발생했는지 추적할 수 있게 해준다. 보통은 에러 발생 시 에러 위치를 알려주므로 자주 사용하지는 않지만, 위치가 나오지 않는다면 사용할만 하다.

## 콘솔

```bash
$ node console
평범한 로그입니다 쉼표로 구분해 여러 값을 찍을 수 있습니다
abc 1 true
에러 메세지는 console.error에 담아주세요
{ outside: { inside: { key: 'value' } } }
{ outside: { inside: [Object] } }
시간 측정: 5.469ms
Trace: 에러 위치 추적
    at b (C:\Users\USER\OneDrive - 광주광역시교육청\바탕 화면\노드 테스트\Global\console.js:26:11)
    at a (C:\Users\USER\OneDrive - 광주광역시교육청\바탕 화면\노드 테스트\Global\console.js:29:3)
    at Object.<anonymous> (C:\Users\USER\OneDrive - 광주광역시교육청\바탕 화면\노드 테스트\Global\console.js:31:1)
    at Module._compile (node:internal/modules/cjs/loader:1275:14)
    at Module._extensions..js (node:internal/modules/cjs/loader:1329:10)
    at Module.load (node:internal/modules/cjs/loader:1133:32)
    at Module._load (node:internal/modules/cjs/loader:972:12)
    at Function.executeUserEntryPoint [as runMain] (node:internal/modules/run_main:83:12)
    at node:internal/main/run_main_module:23:47
전체 시간: 20.977ms
```
