# Section01. JavaScript 기본

## 목차  
* [JavaScript](#javascript)  
* [변수와 상수](#변수와-상수)
* [자료형(타입)](#자료형타입)
* [형 변환(Type Casting)](#형-변환type-casting)
* [연산자(Operator)](#연산자Operator)

---

## JavaScript

JavaScript는 오늘날 가장 많이 사용 되는 프로그래밍 언어


### 웹페이지를 개발하기 위해 만들어진 언어 및 역할

- HTML : 웹페에지에 나타날 요소들의 배치나 모양을 정하기 위해 사용하는 언어
- CSS : 요소들의 스타일을 설정해주는 역할
- Javascript : 정적인 웹사이트에 기능들을 추가해 동적으로 만들어주는 역할

### JavaScript는 어떻게 실행될까?
- JavaScript는 "JavaScript 엔진"에 의해 실행
- JavaScript엔진은 브라우저에 기본 탑재되어 있음
- 따라서 웹 브라우저를 이용하면 간단한 JavaScript 코드를 직접 실행해볼 수 있음

> "JavaScript 엔진"은 게임 구동기(닌텐도) 같이 구동될 수 있게 해주는 거  
크롬이나 사파리 같은 웹브라우저에 탑재되어있음  


Visual Studio Code 단축키
> 개발자 도구 : option + command + i  
라이브 서버 실행 : Command + Shift + P -> Open with Live Server


<br>

## 변수와 상수
: 값을 저장하는 박스

### 변수

- let이라는 키워드로 선언  
`let 변수명 = 값;`
- "변수를 선언한다." = "변수의 초기값을 넣는다." = "변수를 초기화 한다."
```javascript
let age = 30; 
console.log(age);// 30
```
* 변수는 언제든 값을 바꿀 수 있기 때문에 선언할 때 초기화되지 않은 변수 선언 가능  
undefined : "선언되지 않는 값"이라는 뜻  
```javascript
let age2;
console.log(age2); // undefined
```
- let이라는 키워드로 만든 변수는 "이름"으로 서로 구별되기 때문에 중복 선언 불가능
- 변수는 프로그램이 실행되는 도중에 계속해서 값을 바꿔나가며 저장할 수 있는 저장소


### 상수
- const라는 키워드로 선언
`const 변수명 = 값;`
- 변수와 동일하지만 초기화 이후에는 값을 바꿀 수 없음
```javascript
const birth = "1992.03.02"; 
birth = "123";
// console에 오류 발생
```
- 상수 선언 이후 다시는 값을 넣어줄 수 없기 때문에 무조건 선언과 동시에 초기화! 필수!


### 변수 명명규칙(네이밍 규칙)
1. `&`, `_` 제외한 기호는 사용할 수 없다.
2. 숫자로 시작할 수 없다.
3. 예약어(약속된 단어)를 사용할 수 없다.

### 변수 명명 가이드
누가 봐도 알 수 있는 이름으로 하는게 협업에 좋음
```javascript
let salesCount = 1; // 판매량
let refundCount = 1; // 환불량
let totalSalesCount = salesCount - refundCount; // 총 판매량
```

<br>

## 자료형(타입)
### 자료형이란?  
자료형(Type) = 집합   
  : 동일한 속성이나 특징을 가진 원소들을 묶은 것  
  ex. 고양이와 강아지는 "동물"이라는 집합으로 묶임

1. 자료형(DataType)  
   1. 원시 타입  
    - Number
    - String
    - Boolean
    - Null
    - Undefined

   2. 객체 타입
    - Object
       - Array
       - Function
       - RegexExp
  2. 원시타입
  - 기본형 타입이라고도 불림
  - 프로그래밍에 있어 가장 기본적인 값(데이터)들의 타입을 의미함

### 1. Number Type (숫자)
- 정수 `27`
- 실수 `1.5`
- 음수 `-20`
- `Infinity` : 양의 무한대
- `-Infinity` : 음의 무한대
- `NaN` : 넘버 타입. '난'이라고 부름  
  - 수치연산이 실패했을때 결과 값으로 사용  
  - NaN이 있기 때문에 불가능한 수치 연산을 시키더라도 프로그램이 종료되거나 하지 않음
```javascript
console.log(1 * "hello"); // NaN
```
- 사칙연산을 지원  
  - 사칙연산 : `덧셈(+)`, `뺄셈(-)`, `곱하기(*)`, `나누기(/)`, `나머지(%)`  
  - num1 % num2 이렇게 나머지를 구하는 연산은 프로그래밍에서 모듈러 연산이라고 부름


### 2. String Type (문자열)
- 문자열은 쌍따옴표`"`나 작은 따옴표`'`로 감싸야 함  
그렇지 않으면 문자열이 아닌 변수명으로 취급하기 때문에 오류 발생
- 문자열은 덧셈 연산을 지원
```javascript
let myName = "백수진"; 
let myLocation = "수원";
let introduce = myName + myLocation;

console.log(introduce); // 백수진수원
```
- 백틱으로 문자열을 만들 수 있음  
`${변수값}`으로 변수의 값을 동적으로 넣기 가능  
이런 문법을 "템플릿 리터럴 문법"이라고 부름
```javascript
let intorudctText = `${myName}은 ${myLocation}에 거주합니다.`; 
console.log(intorudctText); // 백수진은 수원에 거주합니다.
```

### 3. Boolean Type 
: 참/거짓을 저장하는 타입으로 현재의 상태를 의미

### 4. Null Type
: `아무것도 없다`라는 뜻
```javascript
let empty = null;
console.log(empty); // null
```

### 5. Undefined Type 
: undefined라는 값 하나만 포함하는 특수한 타입
```javascript
let none;
console.log(none); // undefined
```

- undefined는 진짜 변수를 선언하고 아무런 값도 할당하지 않을 때 자동으로 들어가는 값임  
ㄴ 변수를 미쳐 초기화하지 못했거나 존재하지 않음! 어떤 값을 불러오려고 할 때 발생할 수 있는 값
- 반면 null은 개발자가 직접 이 변수에 어떠한 값도 없다를 표현한다!라는 뜻


<br>

## 형 변환(Type Casting)
: 어떤 값의 타입을 다른 타입으로 변경하는 것을 말함  
ex) Number Type인 10을 형 변환해 String Type인 "10"으로 변환

### 1. 묵시적 형 변환(암묵적 형변환)
: 개발자가 직접 설정하지 않아도 알아서 **자바스크립트 엔진**이 형 변환 하는 것을 말함  
: 어떤 타입으로 바꿔줘! 라는 명령을 통해 값의 타입이 변경됨
```javascript
let num = 10;
let str = "20";
const result = num + str;
console.log(result); // 1020
```
* 숫자인 num 변수가 묵시적으로 문자열으로 변환됨
* 숫자 + 문자인 불가능한 연산을 작성하게 되면 자바스크립트 엔진이 오류 발생시키지 않기 위해 숫자를 문자열로 묵시적으로 형을 변환하게 됨
* 그렇다고 모든 불가능한 연산에 이런 묵시적 형 변환이 일어나는것은 아님!  
특정 하나의 변수의값을 형 변환했을때 오류가 발생하지 않고 연산이 잘 종료될 수 있을때만!! 묵시적 형 변환이 일어남


### 2. 명시적 형 변환
: 프로그래머가 내장함수 등을 이용해서 직접 형 변환을 명시  
ㄴ 내장함수란 자바스크립트가 기본적으로 제공하는 함수
1. 문자열 -> 숫자로 변환  
* Number(변수)
```javascript
let str1 = "10";
let strToNum1 = Number(str1);
console.log(10 + strToNum1); // 20
```
* 숫자 외에 다른 문자열 값이 포함되어 있는 문자열을 형 변환할 때에는 변환이 안됨
```javascript
let str2 = "10개"; 
let strToNum2 = Number(str2);
console.log(strToNum2); // NaN
```
* parseInt(변수) : 숫자가 앞쪽으로 나와있어야 함
```javascript
let strToNum2 = parseInt(str2);
console.log(strToNum2); // 10
```

<br>

2. String(변수) : 숫자 -> 문자열로 변환
```javascript
let num1 = 20;
let numToStr1 = String(num1);
console.log(numToStr1 + "입니다."); // 20입니다.
```
<br>

## 연산자(Operator)
: 프로그래밍에서의 다양한 연산을 위한 **기호**, **키워드**를 말함

1. 대입 연산자 `=`
- 변수의 값을 저장할 때 사용하는 가장 기초적인 연산자

2. 산술 연산자
- 덧셈`+`, 뺄셈`-`, 곱셈`*`, 나눗셈`/`, 나누기(모듈러 연산)`%`  
- `*`,`/`,`%` 연산자는 우선순위가 높음

3. 복합 대입 연산자
- 복함되어 있는 대입 연산자(산술 + 대입)
- `num = num + 20;` -> `num+=20;`로 쓸 수 있음
- 대입 연산자 앞에는 모든 산술 연산자 가능

4. 증감 연산자
- 변수 값에서 1만 늘리거나 줄이고 싶을때 사용
- 전위 연산(`++변수`), 후위 연산(`변수++`)
- 모든 산술 연산자로 사용 가능함

5. 논리 연산자
: Boolean 타입(true, false) 타입의 값을 다룰때 사용하는 연산자






<br>

## 조건문

<br>

## 반복문

<br>

## 함수

<br>

## 함수 표현식과 화살표 함수

<br>

## 콜백함수

<br>

## 스코프

<br>

## 객체

<br>

## 배열