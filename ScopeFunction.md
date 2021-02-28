## 📍 Scope Function(화살표 함수)
>1. 화살표 함수 표현은 `function` 표현에 비해 구문이 짧고 자신의 this, arguments, super, new.target을 바인딩하지 않는다.
>2. 화살표 함수는 항상 익명이다.
>3. 함수 표현은 메소드 함수가 아닌 곳에 가장 적합하다.
>4. 생성자로서 사용할 수 없다.
> reference: <a href='https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions/Arrow_functions'>MDN</a>


### ⚡️ Function vs ScopeFunction
화살표 함수는 매개변수가 1개 일 때, 소괄호는 생략가능하다.
화살표 함수 내부에서 바로 `return`하는 경우, 대괄호는 생략가능하다.

사용방법
```javascript
// 인자가 1개 일 때

function square(n){
    return n*n
}

function square(n){
    n*n
}

const square = n => {
    return n*n
}

const square = n => n*n
square(10)

// 인자가 2개 일 때
function sum(a, b){
    return a+b
}

function sum(a, b){
    a+b
}

const sum = (a, b) => {
    return a+b
}

const sum = (a, b) => a+b
```

```javascript
// 객체(object) 선언
const materials = [
  'Hydrogen',
  'Helium',
  'Lithium',
  'Beryllium'
];

```