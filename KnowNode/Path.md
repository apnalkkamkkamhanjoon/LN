# Path

> 폴더와 파일의 경로를 쉽게 조작하도록 도와주는 모듈이다. path 모듈이 필요한 이유 중 하나는 운영체제별로 경로 구분자가 다르기 떄문이다.

## 예제

path.js

```js
const path = require("path");

const string = __filename;

console.log("path.sep : ", path.sep);
console.log("path.delimiter : ", path.delimiter);
console.log("---------------------------------");
console.log("path.dirname() : ", path.dirname(string));
console.log("path.extname() : ", path.extname(string));
console.log("path.basename() : ", path.basename(string));
console.log("path.basename() : ", path.basename(string, path.extname(string)));
console.log("---------------------------------");
console.log("path.parse() : ", path.parse(string));
console.log(
  "path.format() : ",
  path.format({
    dir: "C:\\users\\LN",
    name: "path",
    ext: ".js",
  })
);
console.log("path.normalize() : ", path.normalize("C://users\\\\LN\\path.js"));
console.log("---------------------------------");
console.log("path.isAbsolute() : ", path.isAbsolute("C:\\"));
console.log("path.isAbsolute() : ", path.isAbsolute("./home"));
console.log("---------------------------------");
console.log(
  "path.relative() : ",
  path.relative("C:\\users\\LN\\path.js", "C:\\")
);
console.log(
  "path.join() : ",
  path.join(__dirname, "..", "..", "/users", ".", "/LN")
);
console.log(
  "path.resolve() : ",
  path.resolve(__dirname, "..", "users", ".", "/LN")
);
```

## 콘솔

```bash
$ node path
path.sep :  \
path.delimiter :  ;
---------------------------------
path.dirname() :  C:\Users\USER\OneDrive - 광주광역시교육청\바탕 화면\LN\Test
path.extname() :  .js
path.basename() :  path.js
path.basename() :  path
---------------------------------
path.parse() :  {
  root: 'C:\\',
  dir: 'C:\\Users\\USER\\OneDrive - 광주광역시교육청\\바탕 화면\\LN\\Test',
  base: 'path.js',
  ext: '.js',
  name: 'path'
}
path.format() :  C:\users\LN\path.js
path.normalize() :  C:\users\LN\path.js
---------------------------------
path.isAbsolute() :  true
path.isAbsolute() :  false
---------------------------------
path.relative() :  ..\..\..
path.join() :  C:\Users\USER\OneDrive - 광주광역시교육청\바탕 화면\users\LN
path.resolve() :  C:\LN
```

- path.sep : 경로의 구분자다. Windows는 \, POSIX는 / 이다.
- path.delimiter : 환경 변수의 구분자이다. process.env.PATH를 입력하면 여러 개의 경로가 이 구분자로 구분되어있다. Windows는 세미콜론이고 POSIX는 콜론이다.
- path.dirname(경로) : 파일이 위치한 폴더 경로를 보여준다.
- path.extname(경로) : 파일의 확장자를 보여준다.
- path.basename(경로, 확장자) : 파일의 이름(확장자 포함)을 보여준다. 파일의 이름만 표시하고 싶다면 basename의 두 번째 인자로 파일의 확장자를 넣어주면 된다.
- path.parse(경로) : 파일 경로를 `root, dir, base, ext, name`으로 분리한다.
- path.format(객체) : `path.parse()`한 객체를 파일 경로로 하빈다.
- path.normalize(경로) : /나 \를 실수로 여러번 사용하거나 혼용했을 때 정상적인 경로로 변환해준다.
- path.isAbsolute(경로) : 파일의 경로가 절대경로인지 상대경로인지 `true`나 `false`로 알려준다.
- path.relative(기준경로, 비교경로) : 경로를 두 개 넣으면 첫 번째 경로에서 두 번째 경로로 가는 방법을 알려준다.
- path.join(경로, ...) : 여러 인자를 넣으면 하나의 경로로 합쳐준다. 상대경로인 ..(부모 디렉터리)과 .(현 위치)도 알아서 처리해준다.
- path.resolve(경로) : `path.join`과 비슷하지만 차이가 있다.
