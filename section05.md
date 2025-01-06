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
### JSX란?
- JavaScript Exensions 확장된 자바스크립트 문법
- JavaScript 코드 안에 HTML 코드를 삽입할 수 있게 해줌
- React 애플리케이션의 주요 구조를 담당하며 필요한 컴포넌트를 import하거나 상태를 관리하는 중요한 역할을 함
- 중괄호 안에 JavaScript식을 넣에 JSX 내에서 렌더링 가능
  - jsx에서 JavaScript값을 렌더링 하고 싶다면 중괄호 안에 작성
  - 중괄호 안에는 숫자나 문자열 값으로서 평가될 수 있는 식이라면 무엇이든 넣어줄 수 있음

```javascript
const Main = () => {
  const number = 10;
  return (
    <main>
      <h1>main</h1>
      <h2>{number}</h2>
    </main>
  )
}

export default Main;
```
### JSX 주의 사항
1. 중괄호 내부에는 자바스크립트 표현식만 넣을 수 있다.
2. 숫자, 문자열, 배열 값만 정상적으로 렌더링 된다.
3. 모든 태그는 닫혀있어야 한다.
4. 최상위 태그는 반드시 하나여야만 한다.

Main.jsx가 조건에 따라 각각 다른 UI를 렌더링하도록 생성해보자.
```javascript
const Main = () => {
  const user = {
    name: "백수진",
    isLogin: false,
  };

  return (
    <>
      {user.isLogin ? (<div>로그아웃</div>) : (<div>로그인</div>)}
    </>
  )
}

export default Main;
```
위 코드를 조건문을 이용해 처리
```javascript
if(user.isLogin){
  return <div>로그아웃</div>;
}else{
  return <div>로그인</div>;
}
```

DOM요소에 스타일을 적용하는 방법
1. 요소에 `style`속성 사용
   - style 전달을 위해 객체를 전달
    ```javascript
    if(user.isLogin){
      return <div style={{
        backgroundColor: "red", // css처럼 쓰지 않고 dash(-)없이 연결되는 스타일 + Camelcase 방식으로 써줘야한다.
        borderBottom: "5px solid blue"
      }}>로그아웃</div>;
    }else{
      return <div>로그인</div>;
    }
    ```
2. 별도의 css 파일로 관리
    1. /components/Main.css 생성  
    Main.css
        ```css
        .logout{background-color:red;border-bottom:5px solid green}
        ```
    2. Main.jsx에서 Main.css를 모듈시스템으로 불러오기
        ```javascript
        if(user.isLogin){
          return <div className="logout">로그아웃</div>;
        }else{
          return <div>로그인</div>;
        }
        ```
<br>

## Props로 데이터 전달하기
### Props란?
- 프로퍼티, props(properties의 줄임말)
- 상위 컴포넌트가 하위 컴포넌트에 값을 전달할때 사용한다. 단방향 데이터 흐름을 갖는다.
- 프로퍼티는 수정할 수 없다는 특징이 있다. 자식 입장에선 읽기 전용 데이터이다.

/components/Button.jsx 생성
```javascript
const Button = (props) => {
  return (
    <button style={{color: props.color}}>
      {props.text}
    </button>
  );
}

export default Button;
```

App.jsx
```javascript
import Button from "./components/Button";

function App(){
  return (
    <>
      <Button text={"메일"} color={"red"}/>
      <Button text={"카페"} img={"cafe.png"}>
      <Button text={"블로그"} img={"blog.png"}>
      ...
    </>
  )
}
```
- 부모 컴포넌트에서 자식 컴포넌트에게 props로 전달해주면 이 값들은 객체로 묶여서 자식 컴포넌트의 매개변수로 제공된다.
- 값이 전달되지 않았을 때, 자동으로 설정될 기본 값을 설정해 오류를 해결하자
```javascript
const Button = (props) => {
  return (
    <button style={{color: props.color}}>
      {props.text} - {props.color}
    </button>
  );
}

// 기본 값 설정하기
Button.defaultProps = {
  color: "black",
}

export default Button;
```
- props를 받아서 사용할때 객체의 구조분해할당을 이용해보자  
App.jsx
```javascript
const Button = ({text, color}) => {
  return (
    <button style={{color: color}}>
      {text} - {color}
    </button>
  );
}
```
Button.jsx
- spread 연산자 이용
```javascript
function App() {
  const buttonProps = {
    text: "메일",
    color: "red",
  }
  return (
    <>
      <Button {...buttonProps}/> 
      <Button text={"카페"}/>
      <Button text={"블로그"}/>
    </>
  )
}
```
- props는 문자열이나 자바스크립트 값 뿐만 아니라 HTML요소나 React 컴포넌트도 전달할 수 있다.
- HTML요소를 추가하면 <div> 태그가 자동으로 Button 컴포넌트에 children이라는 props로 전달이 됨  

App.jsx
```javascript
return (
  <>
    <Button {...buttonProps}/> 
    <Button text={"카페"}/>
    <Button text={"블로그"}>
      <div>자식요소</div>
    </Button>
  </>
)
```
Button.jsx
```javascript
const Button = ({text, color, children}) => {
  return (
    <button style={{color: color}}>
      {text} - {color.toUpperCase()}
      {children}
    </button>
  );
}
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