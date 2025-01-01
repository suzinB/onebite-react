# Section03. Node.js 기초

## 목차  
* [Node.js를 소개합니다](#nodejs를-소개합니다)
* [Node.js 설치하기](#nodejs-설치하기)
* [Node.js 사용하기](#nodejs-사용하기)
* [Node.js 모듈 시스템 이해하기](#nodejs-모듈-시스템-이해하기)
* [Node.js 라이브러리 사용하기](#nodejs-라이브러리-사용하기)

---

## Node.js를 소개합니다
- 우리가 배울 React.js는 Node.js를 기반으로 동작하는 기술
- Node.js는 웹 브라우저가 아닌 환경에서도 Javascript 코드를 실행시켜주는 Javascript의 런타임, 즉 Javascript의 실행 환경. 구동기(무언가를 동작시키는 기계나 프로그램)임
- Javascript 히스토리
  - 웹 페이지 내부에 필요한 아주 단순한 기능만을 개발하기 위해 만들어짐
  - 동시대에 존재했던 C언어나 자바 언어와는 다르게 그 문법 자체가 매우 유연하고 작성하기 편리하도록 설계되었음
  - 웹 브라우저 외부에서도 사용해서 프로그램을 만들고 싶다..
  - 2009년도에 Node.js가 등장하면서 JavaScript는 어디서든 동작할 수 있는 범용적인 언어가 되었음
  - Node.js는 Javascript의 전성기를 이끌었다
- Node.js는 아주 단순한 상호작용만 개발할 수 있었던 언어인 Javascript를 범용적으로 사용할 수 있도록 도와주는 Javascript의 실행 환경, 즉 런타임이며
우리가 배우고자 하는 React 또한 이 Node.js를 기반으로 동작하는 기술임

## Node.js 설치하기
### Node.js 설치하기
1. 구글에 Node.js라고 검색
2. 최상단에 있는 공식 홈페이지 접속
3. LTS(Long Term Support, 대부분의 유저들에게 추천하는 현재 가장 안정적인 버전)버전으로 다운받기
4. 설치

### 터미널에서 설치된 노드 버전 확인
`node -v`  
- 맨 앞에 있는 버전이 20점대 이상의 짝수 버전이라면 OK  
- 홀수 버전이거나 20버전의 낮은 버전이면 문제가 발생할 수 있음

### NPM(Node Package Manager) 설치 확인하기
- Node.js의 프로젝트 단위인 패키지를 관리하는 도구
- 새로운 패키지를 생성한다거나 외부 라이브러리를 설치한다거나 삭제하는 기능을 제공



## Node.js 사용하기
### 패키지(Package)
- Node.js에서 사용하는 프로젝트의 단위
- 프로젝트(Project) : 프로그래밍에서 어떠한 목적을 갖는 프로그램을 만들때 사용하는 단위
- Node 패키지를 생성하려면 패키지의 루트 폴더 즉, 패키지의 뿌리가 될 폴더를 하나 만들어줘야함

### 패키지 초기화(생성) `npm init`
- package name: (section03)  
ㄴ 기본값으로 세팅
- version: (1.0.0)  
ㄴ 배포할때 의미가 있음
- description:  
ㄴ 패키지의 간단한 설명
- entry point: (index.js)
- test command:
- git repository:  
...  
- 엔터치면서 생성함
- **package.json**이 생성됨

### 파일 실행
`node {실행할 파일/경로}`
- 패키지 안에 계속해서 코드를 작성하고 새파일을 만들다보면 계속 node로 실행하기는 복잡함
- 이럴때에는 package scripts라는거를 이용하면 좋음

### 패키지 스크립트(package scripts)
- package.json 파일에 이 scripts라는 항목 안에 들어있는 일종의 매크로들
- start라는 스크립트 이름과 실행 명령을 설정
```javascript
"scripts": {
  "test": "echo \"Error: no test specified\" && exit 1",
  "start": "node src/index.js"
},
```
- `npm run start`로 명령을 실행
<br>

## Node.js 모듈 시스템 이해하기
### 모듈 시스템(Module System)이란?
- 모듈(Module) : 기능별로 나뉘어진 이런 각각의 자바스크립트 파일들
- 모듈을 생성하고, 불러오고, 사용하는 등의 모듈을 다루는 다양한 기능을 제공하는 시스템
- JavaScript의 모듈 시스템 : **Common JS(CJS)**, **ES Module(ESM)**, AMD, UDM...

### Common JS(CJS)
- 모듈로부터 특정 값을 내보내고 또 다른 모듈에서 Require로 불러와서 내보내진 값들을 이용할 수 있는 모듈 시스템

`math.js`  
: 계산기능이 있는 js파일 = math 모듈  
: module이라는 객체 안에 각각 프로퍼티로 내보내고 싶은 값들을 넣어줌  
: value값으로 사용되는 변수의 이름과 키 값이 똑같을 경우에는 변수나 함수의 이름만 명시 가능
```javascript
function add(a, b){
  return a + b;
}

function sub(a, b){
  return a - b;
}

module.exports = {
  add, // === add: add,
  sub, // === sub: sub,
}
```
`index.js`  
: math 모듈로부터 add(), sub()를 내보내서 index모듈이 사용할 수 있게 해주자
```javascript
// 내장함수인 require가 현재 경로의 math모듈로부터 객체 형태로 내보내진 값을 반환해줌
const moduleData = require("./math");
console.log(moduleData.add(1,2));
console.log(moduleData.sub(1,2));
console.log(moduleData);
```
`객체의 구조모듈할당`
```javascript
const { add, sub } = require("./math");

console.log(add(1,2));
console.log(sub(1,2));
```

### ESM(ES 모듈 시스템)
- Common JS보다 최신식으로 동작하고 React에서 사용되는 모듈 시스템
- `package.json`의 마지막에 `"type": "module"` 설정(해당 패키지에서 ES 모듈 시스템을 쓰겠다라는 설정을 해줘야함)
- CommonJS 모듈 시스템과 함께 사용할 수 없다

<br>

**math.js**  
: 모듈로부터 어떠한 값을 내보낼때 export라는 키워드 뒤에 객체를 리터럴로 생성해 내보내고 싶은 값을 담아주면 된다  
: 모듈의 확장자까지 꼭 적어줘야한다!
```javascript
function add(a, b){
  return a + b;
}

function sub(a, b){
  return a - b;
}

export { add, sub };
```
**index.js**  
```javascript
import {add, sub} from "./math.js";
```
**함수 선언문 앞에다가 export 선언도 가능**
```javascript
export function add(a, b){
  return a + b;
}

export function sub(a, b){
  return a - b;
}
```
**export default**  
: 모듈을 대표하는 디폴트 값을 내보내는 방법  
: import로 불러올때 중괄호 없이 내보낼 수 있다
: 불러올때 이름을 다르게 설정 가능
```javascript
// math.js
export default function multiply(a, b){
  return a * b;
}

// index.js
import mul from "./math.js";
```
**동일한 경로로부터 값을 불러오는 여러개의 임프트문은 합치기 가능**
```javascript
import mul, {add, sub} from "./math.js";
```
<br>

## Node.js 라이브러리 사용하기
### 라이브러리란?
- 프로그램을 개발할 때 필요한 다양한 기능들을 미리 만들어 모듈화 해 놓은 것
- [npmjs.com](#npmjs.com) : Node.js 라이브러리계의 백화점

**[randomcolor](#https://www.npmjs.com/package/randomcolor)** 라이브러리 설치 및 실습
- 우측 상단에 `Install`에 있는 문구를 터미널에 입력해서 설치
```bash
npm i randomcolor
```
- 설치가 완료되면
  1. `package.json`에 "dependencies"라는 항목 추가됨  
  : dependencies는 의존이라는 뜻, 어떠한 라이브러리를 설치했고 설치된 버전을 보여줌
```javascript
"dependencies": {
  "randomcolor": "^0.6.2"
}
```
  2. `package-lock.json`파일 생성됨  
  : 해당 패키지가 사용하고 있는 라이브러리들의 버전이나 정보를 package.json보다 정확하고 엄밀하게 저장하는 파일
  3. `/node_modules/`폴더 생성됨  
  : 설치한 라이브러리가 실제로 저장되는 곳 

**라이브러리 사용하기**  
`import {라이브러리의 기본값} from "{라이브러리명}`
```javascript
import randomColor from "randomcolor";
const color = randomColor();
console.log(color);
```
- node_modules와 package-lock.json이 삭제되면 오류가 발생 ->  
 `npm install` or `npm i`  
: package.json의 dependencies의 정보를 기준으로 모든 라이브러리를 다시 다 설치해 줌. 그렇기때문에 누군가와 공유할때 node_modules 폴더는 삭제하고 공유해도됨!