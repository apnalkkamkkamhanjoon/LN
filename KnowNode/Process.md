# Process

> `process` 객체는 현재 실행되고 있는 노드 프로세스에 대한 정보를 담고 있다.
> `process` 객체 안에는 다양한 속성이 있다.

## 예제

REPL

```bash
$ node
Welcome to Node.js v19.7.0.
Type ".help" for more information.
> process.version
'v19.7.0'   // 설치된 노드의 버전이다.
> process.arch
'x64'   // 프로세서 아키텍처 정보이다. arm, ia32 등의 값일 수도 있다.
> process.platform
'win32' // 운영체제 플랫폼 정보다. linux나 darwin, freebsd 등의 값일 수도 있다.
> process.pid
16588   // 현재 프로세스의 아이디다. 프로세스를 여러 개 가질 때 구분할 수 있다.
> process.uptime()
59.1072782  // 프로세스가 시작된 후 흐른 시간이다. 단위는 초이다.
> process.execPath
'C:\\Program Files\\nodejs\\node.exe'   // 노드의 경로이다.
> process.cwd()
'C:\\Users\\USER\\OneDrive - 광주광역시교육청\\바탕 화면\\노드 테스트'  // 현재 프로세스가 실행되는 위치이다.
> process.cpuUsage()
{ user: 78000, system: 125000 } // 현재 cpu 사용량이다.
```

사용 빈도는 그리 높지 않지만, 일반적으로 운영체제나 실행 환경별로 다른 동작을 하고 싶을 때 사용한다. `process.env`와 `process.nextTick`, `process.exit()`은 중요하다.

### process.env

> REPL에 `process.env`를 입력하면 매우 많은 정보가 출력된다. 이 정보들은 시스템의 환경 변수임을 알 수 있다.

> `process.env`는 서비스의 중요한 키를 저장하는 공간으로도 사용한다. 서버나 데이터베이스의 비밀번호와 각종 API 키를 코드에 직접 입력하는 것은 위험해, 혹여 서비스가 해킹당해 코드가 유출되었을 때 비밀번호가 코드에 남아 있어 추가 피해가 발생할 수 있어 중요한 비밀번호는 다음과 같이 `process.env`의 속성으로 대체한다.

```js
const secretId = process.env.SECRET_ID;
const secretCode = process.env.SECRET_CODE;
```

`process.env`에 직접 `SECRET_ID`와 `SECRET_CODE`를 넣어주면 된다. 한 번에 모든 운영체제에 동일하게 넣을 수 있는 방법은 `dotenv`를 사용한다.

### process.nextTick(콜백)

> 이벤트 루프가 다른 콜백 함수들보다 `nextTick`의 콜백 함수를 우선으로 처리하도록 만든다.

#### 예제

nextTick.js

```js
setImmediate(() => {
  console.log("immediate");
});
process.nextTick(() => {
  console.log("nextTick");
});
setTimeout(() => {
  console.log("timeout");
}, 0);
Promise.resolve().then(() => console.log("promise"));
```

`process.nextTick`은 `setImmediate`나 `setTimeout`보다 먼저 실행된다. 코드 맨 밑에 `Promise`를 넣은 것은 resolve된 `Promise`도 `nextTick`처럼 다른 콜백들보다 우선시되기 때문이다. 그래서 `process.nextTick`과 `Promise`를 마이크로태스크라고 따로 구분지어 부른다.

#### 콘솔

```bash
$ node nextTick
nextTick
promise
timeout
immediate
```

### process.exit(코드)

> 실행 중인 노드 프로세스를 종료한다. 서벙 이 함수를 사용하면 서버가 멈추므로 서버에는 거의 사용하지 않는다. 하지만 서버 외의 독립적인 프로그램에서는 수동으로 노드를 멈추게 하지 않기 위해 사용한다.

#### 예제

`setInterval`로 반복되고 있는 코드를 `process.env`로 멈춘다.

exit.js

```js
let i = 1;
setInterval(() => {
  if (i == 5) {
    console.log("종료!");
    process.exit();
  }
  console.log(i);
  i += 1;
}, 1000);
```

1부터 4까지 표시한 뒤, i가 5가 되었을 때 종료된다.

#### 콘솔

```bash
$ node exit
1
2
3
4
종료!
```

> process.exit 메서드는 인자로 코드 번호를 줄 수가 있다. 인자를 주지 않거나 0이면 정상 종료를 뜻하고, 1을 주면 비정상 종료를 뜻한다. 만약 에러가 발생해서 종료하는 경우에는 1을 넣어주면 된다.
