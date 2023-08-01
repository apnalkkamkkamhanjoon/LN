# Os

> os 모듈은 웹 브라우저에 사용되는 자바스크립트는 운영체제의 정보를 가져올 수 없지만, 노드는 os 모듈에 정보가 담겨 있어 정보를 가져올 수 있다.

## 예제

os의 대표적인 메서드다.

os.js

```js
const os = require("os");

console.log("운영체제 정보-------------------------");
console.log("os.arch() : ", os.arch());
console.log("os.platform() : ", os.platform());
console.log("os.type() : ", os.type());
console.log("os.uptime() : ", os.uptime());
console.log("os.hostname() : ", os.hostname());
console.log("os.release() : ", os.release());

console.log("경로---------------------------------");
console.log("os.homedir() : ", os.homedir());
console.log("os.tmpdir() : ", os.tmpdir());

console.log("cpu 정보-----------------------------");
console.log("os.cpus() : ", os.cpus());
console.log("os.cpus().length : ", os.cpus().length);

console.log("메모리 정보---------------------------");
console.log("os.freemem() : ", os.freemem());
console.log("os.totalmem() : ", os.totalmem());
```

## 콘솔

```bash
$ node os
운영체제 정보-------------------------
os.arch() :  x64
os.platform() :  win32
os.type() :  Windows_NT
os.uptime() :  649154.078
os.hostname() :  DESKTOP-HGNEA2U
os.release() :  10.0.22621
경로---------------------------------
os.homedir() :  C:\Users\USER
os.tmpdir() :  C:\Users\USER\AppData\Local\Temp
cpu 정보-----------------------------
os.cpus() :  [
  {
    model: '11th Gen Intel(R) Core(TM) i7-1165G7 @ 2.80GHz',
    speed: 2803,
    times: {
      user: 5940859,
      nice: 0,
      sys: 5040234,
      idle: 560274546,
      irq: 536046
    }
  },
  {
    model: '11th Gen Intel(R) Core(TM) i7-1165G7 @ 2.80GHz',
    speed: 2803,
    times: {
      user: 3331906,
      nice: 0,
      sys: 1817453,
      idle: 566106281,
      irq: 51343
    }
  },
  {
    model: '11th Gen Intel(R) Core(TM) i7-1165G7 @ 2.80GHz',
    speed: 2803,
    times: {
      user: 5390390,
      nice: 0,
      sys: 2290796,
      idle: 563574187,
      irq: 69781
    }
  },
  {
    model: '11th Gen Intel(R) Core(TM) i7-1165G7 @ 2.80GHz',
    speed: 2803,
    times: {
      user: 3548953,
      nice: 0,
      sys: 1393140,
      idle: 566313281,
      irq: 36312
    }
  },
  {
    model: '11th Gen Intel(R) Core(TM) i7-1165G7 @ 2.80GHz',
    speed: 2803,
    times: {
      user: 2543187,
      nice: 0,
      sys: 1830093,
      idle: 566882093,
      irq: 34109
    }
  },
  {
    model: '11th Gen Intel(R) Core(TM) i7-1165G7 @ 2.80GHz',
    speed: 2803,
    times: {
      user: 2404343,
      nice: 0,
      sys: 1564984,
      idle: 567286046,
      irq: 27750
    }
  },
  {
    model: '11th Gen Intel(R) Core(TM) i7-1165G7 @ 2.80GHz',
    speed: 2803,
    times: {
      user: 2126828,
      nice: 0,
      sys: 1397859,
      idle: 567730687,
      irq: 21781
    }
  },
  {
    model: '11th Gen Intel(R) Core(TM) i7-1165G7 @ 2.80GHz',
    speed: 2803,
    times: {
      user: 1876968,
      nice: 0,
      sys: 1088046,
      idle: 568290359,
      irq: 17296
    }
  }
]
os.cpus().length :  8
메모리 정보---------------------------
os.freemem() :  1113673728
os.totalmem() :  8247590912
```

> `process` 객체와 겹치는 부분도 조금 보인다. `os`도 사용자 컴퓨터의 운영체제 정보를 가져오는 것이다.

- os.arch() : `process.arch`와 동일하다.
- os.platform() : `process.platform`과 동일하다.
- os.type() : 운영체제의 종류를 보여준다.
- os.uptime() : 운영체제 부팅 이후 흐른 시간(초) 를 보여준다. `process.uptime()`은 노드의 실행 시간이다.
- os.hostname() : 컴퓨터의 이름을 보여준다.
- os.release() : 운영체제의 버전을 보여준다.
- os.homedir() : 홈 디렉터리 경로를 보여준다.
- os.cpus() : 컴퓨터의 코어 정보를 보여준다.
- os.freemem() : 사용 가능한 메모리(RAM)을 보여준다.
- os.totalmem() : 전체 메모리 용량을 보여준다.

> 여기에는 없지만 `os.constants`라는 객체가 있다. 그 안에는 각종 에러와 신호에 대한 정보가 담겨있다. 에러가 발생했을 때, `EADDRINUSE`나 `ECONNRESET` 같은 에러 코드를 함께 보여준다.

> os 모듈은 주로 컴퓨터 내부 자원에 빈번하게 접근하는 경우에 사용된다. 즉, 일반적인 웹 서비스를 제작할 때는 사용 빈도가 높지 않다. 하지만 운영체제별로 다른 서비스를 제공하고 싶을 때 os 모듈이 유용할 것이다.
