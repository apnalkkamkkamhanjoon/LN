# **filename, **dirname

> 노드에서는 파일 사이에 모듈 관계가 있는 경우가 많아 현재 파일의 경로나 파일명을 알아야하는 경우가 있다. 노드는 `__filename`, `__dirname`이라는 키워드로 경로에 대한 정보를 제공한다. 파일에 `__filename`과 `__dirname`을 넣어두면 실행 시 현재 파일명과 파일 경로로 바뀐다.

## 예제

filename.js

```js
console.log(__filename);
console.log(__dirname);
```

## 콘솔

```js
$ node filename.js
C:\Users\USER\OneDrive - 광주광역시교육청\바탕 화면\노드 테스트\Global\filename.js
C:\Users\USER\OneDrive - 광주광역시교육청\바탕 화면\노드 테스트\Global
```
