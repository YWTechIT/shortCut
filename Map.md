## 📍 Map
> 1. `map()` 메소드는 배열 내의 모든 요소 각각에 대하여 주어진 함수를 호출한 결과를 모아 새로운 배열(list)을 반환한다.
> 2. `callback` 함수는 호출될 때 대상 요소의 값, 그 요소의 인덱스, 그리고 `map`을 호출한 원본 배열 3개의 인수를 전달받는다.
> 3. `map`은 호출한 배열의 값을 변형하지 않는다. `callback`에 의해 변형될 수는 있다.

```javascript
// 배열
const fruits = ['apple', 'banana', 'kiwi', 'orange']

console.log(fruits.map(fruit => fruit))
👉🏽 ["apple", "banana", "kiwi", "orange"]0: "apple"1: "banana"2: "kiwi"3: "orange"

// 배열에 들어있는 숫자들을 제곱해서 새로운 배열을 만들기
const numbers = [1, 2, 3, 4, 5]

console.log(numbers.map(number => number * number))
👉🏽 (5) [1, 4, 9, 16, 25]
```
