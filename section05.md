# Section05. React.js 입문

## 목차  
* [실습 준비하기](#실습-준비하기)
* [React 컴포넌트](#react-컴포넌트)
* [JSX로 UI 표현하기](#jsx로-ui-표현하기)
* [Props로 데이터 전달하기](#props로-데이터-전달하기)
* [이벤트 처리하기](#이벤트-처리하기)
* [State로 상태관리하기](#state로-상태관리하기)
* [State와 Props](#state와-props)
---
* [State로 사용자 입력 관리하기 1](#state로-사용자-입력-관리하기-1)
* [State로 사용자 입력 관리하기](#state로-사용자-입력-관리하기)
* [useRef로 컴포넌트의 변수 생성하기](#useref로-컴포넌트의-변수-생성하기)
* [React Hooks](#react-hooks)

---

## 실습 준비하기
1. section05 프로젝트 생성 후 `/src/assets/vite.svg`, `/public/react.svg` 삭제
2. `App.jsx`의 불필요한 구문 삭제
```javascript
import './App.css'

function App() {
  return (
    <>
    </>
  )
}

export default App
```
3. `App.css`, `index.css` 안의 내용 삭제
4. `main.js`의 `<StrictMode>` 구문 삭제
  - StrictMode는 개발 모드로 리액트 앱을 실행하고 있을때 코드를 내부적으로 검사해 경고해주는 도구. 실습에서는 필요없고 입문자들의 혼란을 유발시킬 수 있기 때문에 삭제.
5. VS Code 확장자에서 ESLint 설치 : 정적으로 검사해서 오류가 발생할 만한 코드가 있으면 경고를 띄워줌
  - 강의와 똑같은 .eslintrc.cjs가 아니라 eslint.config.js가 설치됨 -> 상관 없다는 [선생님 답변](https://www.inflearn.com/community/questions/1353483)
  - rules 하위에 코드 추가해 실습에 혼란스럽지 않게 해주기
```javascript
rules: {
      ...
      'react-refresh/only-export-components': [
        'warn',
        { allowConstantExport: true },
      ],
      "no-unused-vars":"off", // 코드상에 사용하지 않는 변수가 있을때 알려주는 옵션
      "react/prop-types":"off", // 안전하게 사용할 수 있도록 해주는 옵션
    },
```
<br>

## React 컴포넌트
### 컴포넌트란?
- component : HTML 태그를 반환하는 함수로 함수의 이름을 따서 {함수이름} compoent라고 부름
- 함수의 이름은 첫글자가 **대문자**여야만 React에서 컴포넌트로 인정

App.jsx에 Header 컴포넌트 생성
```javascript
function Header(){
  return(
    <header>
      <h1>header</h1>
    </header>
  )
}
```
화살표 함수로도 가능
```javascript
const Header = () => {
  return(
    <header>
      <h1>header</h1>
    </header>
  )
}
```

- `main.jsx`에서 render() 메서드를 통해 화면을 렌더링을 하고 있는 컴포넌트는 App 컴포넌트임
- App()의 return문 안에 Header 컴포넌트를 배치해주면 App 컴포넌트가 화면에 렌더링 될때 Header 컴포넌트의 반환 값을 불러와서 렌더링 시켜주게 됨
```javascript
function App() {
  return (
    <>
      <Header />
      <h1>안녕 리액트!</h1>
    </>
  )
}
```
- 결론
  - React의 모든 컴포넌트들은 화면에 렌더링되기 위해서 App 컴포넌트의 **자식 컴포넌트**로 존재해야함. 
  - 모든 컴포넌트는 App 컴포넌트를 최상위 조상으로 갖는 **계층 구조**를 갖음
  - 이 App 컴포넌트를 **Root 컴포넌트**라고 부름. *App 말고 다른 이름으로도 사용 가능하지만 관례적으로 App으로 부름*
- 모듈화를 위해 컴포넌트별로 파일을 나눔
  1. `/component/` 폴더 생성
  2. `Header.jsx`파일 생성
```javascript
const Header = () => {
  return(
    <header>
      <h1>header</h1>
    </header>
  )
}

export default Header;
```
  3. `App.jsx`에 `import Header from "./components/Header.jsx";` 코드 추가  
    - ES 모듈 시스템으로 불러오고 있더라도 .jsx 확장자 삭제 가능  
    - vite로 만든 React app에서는 확장자를 안 써도 자동으로 파일을 찾아가도록 설정 되어있기 때문
  4. 같은 방식으로 `Main.jsx`, `Footer.jsx` 파일 생성해 `App.jsx`에서 불러옴
  `Main.jsx`
```javascript
const Main = () => {
  return (
    <main>
      <h1>main</h1>
    </main>
  )
}

export default Main;
```
  `Footer.jsx`
```javascript
const Footer = () => {
  return (
    <footer>
      <h1>footer</h1>
    </footer>
  )
}

export default Footer;
```
  `App.jsx`
```javascript
import './App.css'
import Header from "./components/Header.jsx";
import Main from "./components/Main.jsx";
import Footer from "./components/Footer.jsx";

function App() {
  return (
    <>
      <Header />
      <Main />
      <Footer />
    </>
  )
}

export default App;
```
<br>

## JSX로 UI 표현하기
```javascript
```
<br>

## Props로 데이터 전달하기
```javascript
```
<br>

## 이벤트 처리하기
```javascript
```
<br>

## State로 상태관리하기
```javascript
```
<br>

## State와 Props
```javascript
```
<br>
---------

## State로 사용자 입력 관리하기 1
```javascript
```
<br>

## State로 사용자 입력 관리하기
```javascript
```
<br>

## useRef로 컴포넌트의 변수 생성하기
```javascript
```
<br>

## React Hooks
```javascript
```
<br>