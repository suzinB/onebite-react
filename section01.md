# Section01. JavaScript 기본

## 목차  
* [JavaScript](#javascript)  
* [변수와 상수](#변수와-상수)
* [자료형(타입)](#자료형타입)
* [형 변환(Type Casting)](#형-변환type-casting)
* [연산자(Operator)](#연산자Operator)
* [조건문](#조건문)
* [반복문(Loop, Iteration)](#반복문Loop,Iteration)
* [함수](#함수)
* [함수 표현식과 화살표 함수](#함수-표현식과-화살표-함수)

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
   1. Or 연산자  
   : 값이 하나만 참이어도 참이 됨  
   `let or = true || false; // true`
   2. And 연산자  
   : 양쪽이 다 참이어야 참이 됨
   `let and = true && false; // false`
   3. Not 연산자  
   : 참이라면 거짓, 거짓이라면 참으로 변경됨
   `let not = !true; // false`

6. 비교 연산자  
: 2개의 값을 서로 비교하는 연산자
   * 동등 비교 연산자  
  `let comp1 = 1 === 2; //false`
   * 비동등 비교 연산자  
  `let comp2 = 1 !== 2; //true`  
      * 왜 `===` 3개를 쓰는가?  
        : 2개`==`만 쓰면 자료형까지 같은지는 비교할 수 없기 때문에, 자료형이 다를때는 다른 값으로 보기때문에 3개`===`를 쓰는게 권장되는 방식임!
   * 대소 비교 : `>`, `<`, `>=`, `<=`


7. null 병합 연산자  
: 존재하는 값을 추려내는 기능으로 null이나 undefined를 제외한 것들을 찾아내는 연산자
```javascript
let var1;
let var2 = 10;
let var3 = 20;
let var4 = var1 ?? var2; 
console.log(var4); // 10
```
ㄴ var1은 초기화가 되지않은 undefined, var2는 초기화가 된 값이므로  
null병합 연산자`??`가 이 두 피연산자(연산에 참여하는 값) 중 undefined가 아닌 var2의 값을 찾아서 var4에 대입
```javascript
let var5 = var2 ?? var3; 
console.log(var5); // 10
```
ㄴ 두 피연산자가 둘다 null이나 undefined가 아니다라고 하면 처음에 적힌 값이 반환됨

* 실무에서 쓰이는 방법  
 : 회원 관리 시스템에서 userName이 있다면 userName을 displayName으로 저장, 없다면 userNickName을 저장해라
```javascript
let userName = "백수진";
let userNickName = "suzin"
let displayName = userName ?? userNickName; 
```

<br>

8. typeof 연산자  
: 값의 타입을 문자열로 반환하는 기능을 하는 연산자
```javascript
var7 = "hello";
let t1 = typeof var7;
console.log(t1); // boolean
```


9. 삼항 연산자  
: 3개의 항을 사용해 조건식을 이용해서 `참`이나 `거짓`일 때의 값을 반환  
`조건식` ? `참일때값` : `거짓일때값`
```javascript
// 요구사항 : 변수 res에 var8의 값이 짝수일때는 "짝수", 홀수일대는 "홀수"를 저장해라
let var8 = 10;
let res = var8 % 2 === 0 ? "짝수" : "홀수";
console.log(res); // 짝수
```

<br>

## 조건문
### 조건문(Condetional Statement)이란?
 - 특정 조건을 만족했을 때에만 실행되는 코드를 작성하기 위한 문법
- 대표적인 조건문 : if, switch
  * 복잡한 여러개의 조건을 이용하고 싶을때는 if문
  * 어떠한 변수의 값을 기준으로 각각 다른 코드를 실행시키고 싶을때는 switch문

1. if 조건문(if문)
- if로 시작해서 else로 끝나야함
```javascript
if(조건식){
  //조건식이 만족했을때 수행할 코드
}else if(조건식){ // 그 다음 조건식
  //조건식이 만족했을때 수행할 코드
}else{ //그렇지 않으면 이라는 뜻
  // 조건이 거짓일때 수행할 코드
}
```

2. switch 조건문
- 기능 자체는 if문과 동일하게 조건에 따라 다른 코드를 실행할 수 있게 도와줌
- 다수의 조건을 처리할때 if문보다 더 직관적
- 변수의 값과 일치하는 케이스를 위에서부터 아래로 차례대로 탐색하다가 일치하는 케이스를 만나면 그 아래에 있는 모든 코드를 다 수행시켜줌
- 일치하는 케이스에서 맞추려면 `break;`
- 예외 케이스는 `default:`
```javascript
let animal = "owl";
switch (animal){
  case "cat" : {
    console.log("고양이");
    break;
  }
  case "dog" :{
    console.log("강아지");
    break;
  }
  case "bear" :{
    console.log("곰");
    break;
  }
  case "snake" :{
    console.log("뱀");
    break;
  }
  case "tiger" :{
    console.log("호랑이");
    break;
  }
  default:{
    console.log(animal+"은 모릅니다")
  }
}
```

<br>

## 반복문(Loop, Iteration)  
: 어떠한 동작을 반복해서 수행할 수 있도록 만들어 주는 문법 
* for문
   * 초기식 : 반복문 내에서 만 쓸 수 있는 변수. counter 변수라고도 불림
   * 조건식 : 반복문이 언제까지 반복할 건지 설정하는 식 - 참일때에만 계속 반복 되고 거짓이 되면 종료가 됨
   * 증감식 : 한번의 반복이 종료될때마다 증감시키는 식, 증감연산자를 이용함
```javascript
for (초기식; 조건식; 증감식){
  반복할 코드
}
```
* continue  
: 반복문 내에서 다른 코드들을 실행하지 ㅇ낳고 바로 다음 반복회차로 넘어감
```javascript
for (let idx = 1; idx < 10; idx++){
  if(idx % 2 === 0){
    continue;
  }
  console.log(idx);
}
// 1
// 3
// 5
// 7
```
* break  
: 조건식이 거짓이 되지 않았을때에도 강제로 종료하는 방법 (조건식을 바꿀 수 없을 때)
```javascript
for (let idx = 1; idx < 10; idx++){
  if(idx > 3){
    break;
  }
  console.log(idx);
}
// 1
// 2
// 3
```
<br>

## 함수
1. 함수를 사용하는 이유
- 중복된 코드를 코드를 재사용(한 번 정의 후 여러번 사용)할 수 있다
- 다른 인자를 사용하여 동일한 코드를 사용하고 다른 결과를 도출할 수 있다.

2. 함수의 특징
- 함수가 값이기 때문에 변수 안에 담길 수 있다.
- 객체의 속성안에 method로 담길 수 있다.
- 다른 함수의 인자값을 전달할 수 있다.
- 함수의 return값으로도 사용할 수 있다.
- 배열의 값으로도 사용할 수 있다.

3. 함수 선언 및 호출
```javascript
// 1. 함수 선언
function 함수명(){
  // 실행할 코드
}

// 2. 함수 호출
// 함수를 호출할 때에는 소괄호()와 함께 호출
greeting();
```
4. 동적인 함수 생성  
* 함수를 호출하면서 함수에게 전달하는 값을 **인수**라고 함
* 소괄호()안에 함수의 변수를 선언해 전달된 인수들을 순서대로 저장하는 변수들을 **매개변수**라고 함

* `return`: 함수 호출의 결과 값으로 return문을 만나면 함수는 값을 반환하고 종료되어 하위 코드들은 수행되지 않음
```javascript
function getArea(width, height){
  let area = width * height;
  return area;
}
let area1 = getArea(10,20);
console.log(area1); // 200
```
* 중첩함수 : 함수 내부에 선언된 함수
```javascript
function getArea(width, height){
  function another(){ //중첩 함수
    consoel.log("another");
  }
  let area = width * height;
  return area;
}
```
<br>

5. Javascript 함수 호이스팅  
- 함수의 선언을 함수의 호출보다 아래에 두어도 문제없이 잘 수행됨
- 호이스팅이라는 건 우리말로 `끌어올리다`라는 뜻을 같고 있음
- 함수 선언이 무조건 위에 있지 않아도 되기 때문에 좀 더 유연하게 프로그래밍 할 수 있음

<br>

## 함수 표현식과 화살표 함수
### 함수 표현식
1. 함수 선언
* 호이스팅 됨
* 자바스크립트에서는 함수도 하나의 값으로 취급
```javascript
function funcA(){
  console.log("funcA 호출함");
}

let varA = funcA;
console.log(varA); // 함수 자체를 변수 선언함. 

// function funcA(){
//   console.log("funcA 호출함");
// }
```
* 함수를 어떤 변수에 담게 되면 이 변수의 이름으로 함수를 호출할 수 있음
```javascript
varA();

// funcA 호출함
```

2. 익명함수(이름이 없다)
* 호이스팅 되지 않음
```javascript
let varB = function funcB(){ // 함수를 만들자마자 바로 변수에 담는것도 가능
  console.log("funcB 호출함");
}
varB();

//funcB 호출함
```
* funcB의 경우 선언식이 아니라 값으로 함수가 생성된 것이기 때문에 함수의 이름으로 호출 불가 `funcB();`로 선언하면 오류남
* 결국 funcB라는 함수로 부르지 못하기때문에 funcB를 생략할 수 있음
```javascript
let varB = function (){ // 함수를 만들자마자 바로 변수에 담는것도 가능
  console.log("funcB 호출함");
}
```

### 화살표 함수
* 함수를 이전보다 더 빠르고 간결하게 생성해 줄 수 있도록 도와주는 JavaScript 문법
* 익명함수에서 function을 지우고 소괄호와 중괄호 사이에 화살표를 넣어줌
```javascript
let varC = () => {
  return 1;
}
```
* 여기서 더 간결하게 만들 수도 있음
* 그냥 값을 반환하기만 하는 함수라면 중괄호랑 return문도 지워주면 됨
```javascript
let varC = () => 1;
console.log(varC()); // 1
```
* 소괄호 안에 매개변수 선언도 가능
```javascript
let varD = (value) => value + 10;
console.log(varD(10)); // 20
```
* 익명함수에서 추가적인 작업이 더 필요하다면 중괄호`{}`를 이용해 가능
```javascript
let varE = (value) => {
  console.log(value);
  return value++;
}
console.log(varE(10));
// 10
// 11
```

<br>

## 콜백함수
```javascript
```
<br>

## 스코프
```javascript
```
<br>

## 객체
```javascript
```
<br>

## 배열
```javascript
```