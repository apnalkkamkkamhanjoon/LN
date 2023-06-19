# REPL

> Read(읽고), Eval(해석하고), Print(반환하고), Loop(반복하고) 라는 의미를 가지고있어 REPL(Read Eval Print Loop)이라 부른다.

## 사용

> REPL은 한두 줄짜리 코드를 테스트해보는 용도로는 좋지만
> 여러 줄의 코드를 실행하기에는 불편해, 여러 줄의 코드는 자바스크립트 파일로 만든 후 파일을 통쨰로 실행하는 것이 좋다.

## 예제

```js
> const str = 'Hello world, hello node';
undefined

> console.log(str);
HelloWorld, hello node
Undefined
>
```

## JS 파일로 실행하기

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