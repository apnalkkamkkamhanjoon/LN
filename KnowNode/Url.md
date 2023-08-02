# url

> 인터넷 주소를 쉽게 조작하도록 도와주는 모듈이다. url 처리에는 크게 두 가지 방식이 있다. WHATWG(웹 표준을 정하는 단체의 이름)방식의 url과 예전부터 노드에서 사용하던 방식의 url이 있다.

## 예제

url.js

```js
const url = require("url");

const URL = url.URL;
const myURL = new URL(
  "http://www.gilbut.co.kr/book/bookList.aspx?/sercate1=00100100#anchor"
);
console.log("new URL() : ", myURL);
console.log("url.format() : ", url.format(myURL));
console.log("----------------------------------");
const parsedUrl = url.parse(
  "http://www.gilbut.co.kr/book/bookList.aspx?/sercate1=00100100#anchor"
);
console.log("url.parse() : ", parsedUrl);
console.log("url.format() : ", url.format(parsedUrl));
```

## 콘솔

```bash
$ node url
new URL() :  URL {
  href: 'http://www.gilbut.co.kr/book/bookList.aspx?/sercate1=00100100#anchor',
  origin: 'http://www.gilbut.co.kr',
  protocol: 'http:',
  username: '',
  password: '',
  host: 'www.gilbut.co.kr',
  hostname: 'www.gilbut.co.kr',
  port: '',
  pathname: '/book/bookList.aspx',
  search: '?/sercate1=00100100',
  searchParams: URLSearchParams { '/sercate1' => '00100100' },
  hash: '#anchor'
}
url.format() :  http://www.gilbut.co.kr/book/bookList.aspx?/sercate1=00100100#anchor
----------------------------------
url.parse() :  Url {
  protocol: 'http:',
  slashes: true,
  auth: null,
  host: 'www.gilbut.co.kr',
  port: null,
  hostname: 'www.gilbut.co.kr',
  hash: '#anchor',
  search: '?/sercate1=00100100',
  query: '/sercate1=00100100',
  pathname: '/book/bookList.aspx',
  path: '/book/bookList.aspx?/sercate1=00100100',
  href: 'http://www.gilbut.co.kr/book/bookList.aspx?/sercate1=00100100#anchor'
}
url.format() :  http://www.gilbut.co.kr/book/bookList.aspx?/sercate1=00100100#anchor
```

- url.parse(주소) : 주소를 분해한다. WHATWG 방식과 비교하면 `username`과 `password`대신 `auth`속성이 있고, `searchParams`대신 `query`가 있다.
- url.format(객체) : WHATWG 방식의 url과 기존 노드의 url 모두 사용할 수 있다. 분해되었던 url 객체를 다시 원래 상태로 조립한다.

## 예제2

searchParams.js

```js
const { URL } = require("url");

const myURL = new URL(
  "https://www.gilbut.co.kr/?page=3&limit=10&category=nodejs&category=javascript"
);
console.log("searchParams : ", myURL.searchParams);
console.log("searchParams.getAll() : ", myURL.searchParams.getAll("category"));
console.log("searchParams.get() : ", myURL.searchParams.get("limit"));
console.log("searchParams.has() : ", myURL.searchParams.has("page"));

console.log("searchParams.keys() : ", myURL.searchParams.keys());
console.log("searchParams.values() : ", myURL.searchParams.values());

myURL.searchParams.append("filter", "es3");
myURL.searchParams.append("filter", "es5");
console.log(myURL.searchParams.getAll("filter"));

myURL.searchParams.set("filter", "es6");
console.log(myURL.searchParams.getAll("filter"));

myURL.searchParams.delete("filter");
console.log(myURL.searchParams.getAll("filter"));

console.log("searchParams.toString() : ", myURL.searchParams.toString());
myURL.search = myURL.searchParams.toString();
```

## 콘솔2

```bash
$ node url
new URL() :  URL {
  href: 'http://www.gilbut.co.kr/book/bookList.aspx?/sercate1=00100100#anchor',
  origin: 'http://www.gilbut.co.kr',
  protocol: 'http:',
  username: '',
  password: '',
  host: 'www.gilbut.co.kr',
  hostname: 'www.gilbut.co.kr',
  port: '',
  pathname: '/book/bookList.aspx',
  search: '?/sercate1=00100100',
  searchParams: URLSearchParams { '/sercate1' => '00100100' },
  hash: '#anchor'
}
url.format() :  http://www.gilbut.co.kr/book/bookList.aspx?/sercate1=00100100#anchor
----------------------------------
url.parse() :  Url {
  protocol: 'http:',
  slashes: true,
  auth: null,
  host: 'www.gilbut.co.kr',
  port: null,
  hostname: 'www.gilbut.co.kr',
  hash: '#anchor',
  search: '?/sercate1=00100100',
  query: '/sercate1=00100100',
  pathname: '/book/bookList.aspx',
  path: '/book/bookList.aspx?/sercate1=00100100',
  href: 'http://www.gilbut.co.kr/book/bookList.aspx?/sercate1=00100100#anchor'
}
url.format() :  http://www.gilbut.co.kr/book/bookList.aspx?/sercate1=00100100#anchor

USER@DESKTOP-HGNEA2U MINGW64 ~/OneDrive - 광주광역시교육청/바탕 화면/LN/Test (main)
$ node searchParams
searchParams :  URLSearchParams {
  'page' => '3',
  'limit' => '10',
  'category' => 'nodejs',
  'category' => 'javascript' }
searchParams.getAll() :  [ 'nodejs', 'javascript' ]
searchParams.get() :  10
searchParams.has() :  true
searchParams.keys() :  URLSearchParams Iterator { 'page', 'limit', 'category', 'category' }
searchParams.values() :  URLSearchParams Iterator { '3', '10', 'nodejs', 'javascript' }
[ 'es3', 'es5' ]
[ 'es6' ]
[]
searchParams.toString() :  page=3&limit=10&category=nodejs&category=javascript
```

> URL 생성자를 통해 `myURL`이라는 주소 객체를 만들었다. `myURL`안에는 `searchParams` 객체가 있다. 이 객체는 `search` 부분을 조작하는 다양한 메서드를 지원한다.

- getAll(키) : 키에 해당하는 모든 값들을 가져온다. `category` 키에는 두 가지 값, 즉 `nodejs`와 `javascript`의 값이 들어 있다.
- get(키) : 키에 해당하는 첫 번째 값만 가져온다.
- has(키) : 해당 키가 있는지 없는지를 검사한다.
- key() : `searchParams`의 모든 키를 반복기 객체로 가져온다.
- values() : `searchParams`의 모든 값을 반복기 객체로 가져온다.
- append(키, 값) : 해당 키를 추가한다. 같은 키의 값이 있다면 유지하고 하나 더 추가한다.
- set(키, 값) : `append`와 비슷하지만 같은 키의 값들을 모두 지우고 새로 추가한다.
- delete(키) : 해당 키를 제거한다.
- toString() : 조작한 `searchParams` 객체를 다시 문자열로 만든다. 이 문자열을 `search`에 대입하면 주소 객체에 반영된다.

> `query` 같은 문자열보다 `searchParams`가 유용한 이유는 `query`의 경우 querysting 모듈을 한 번 더 사용해야 하기 떄문이다.
