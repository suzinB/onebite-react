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
```javascript
```
<br>

## Node.js 라이브러리 사용하기
```javascript
```
<br>