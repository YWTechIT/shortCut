## 📍 Destructuring assignment
> 배열이나 객체의 속성을 해체하여 그 값을 개별 변수에 담을 수 있게 하는 JS표현식
> reference: <a href='https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment'>MDN</a>

### ⚡️ 기본변수할당
객체 내에 있는 변수값들을 외부로 꺼내려고 할때, `.`, `[]`로 객체의 이름으로 접근하여 값을 가져올 수 있다.
하지만, 이 과정에서 변수를 중복하여 사용하고, 가져와야하는 속성이 많아 질수록 코드의 중복이 많아진다.
이때 주의해야 할 점은 <span style='color:blue'>중괄호 안에 추가된 속성명을 사용해야한다.</span>

객체에서 정의된 변수명을 변경하고 싶을때는 `{속성명: 새로운 변수명}`을 입력하여 변경 할 수 있다.
이때는 `객체`처럼 `key값`이 없기때문에 순서에 맞춰 선언하면된다.

비구조할당은 배열에서 `[]`를, 객체에서는 `{}`를 사용하는 점을 잊지말자.

```javascript
// 배열: 비구조 할당
const foo = ['one', 'two', 'three'];
const [one, two] = foo;

console.log(one)
console.log(two)

// 객체: 비구조 할당
const info = {
    name: 'AYW',
    age: 27,
    address: 'Hwaseong',
    phone: '010-1234-1234'
}

console.log(info.name)
console.log(info.age)
console.log(info.address)
console.log(info.phone)

const {name, age, address, phone} = info;
console.log(name)
console.log(age)
console.log(address)
console.log(phone)
```