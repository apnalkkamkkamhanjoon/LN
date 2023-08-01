# JS 파일로 실행하기

> REPL에 직접 코드를 입력하는 대신 자바스크립트 파일을 만들어 실행한다.
> helloWorld.js

```js
function helloWorld() {
  console.log("Hello World");
  helloNode();
}
function helloNode() {
  console.log("Hello Node");
}
helloWorld();
```

콘솔에서 node로 실행한다. REPL이 아닌 콘솔에서 입력하는 것이다.
**콘솔**

```bash
& node helloWorld
Hello World
Hello Node
```
