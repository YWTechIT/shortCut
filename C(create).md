## 📍 C(create)
1. `input: e.target.value`
2. `useCallback` 선언 후 `input`값 넣기

```javascript
const App = () => {
    const [input, setInput] = useState('');

    const onChange = useCallback(e => {
        setInput(e.target.value)
    }, [])

    return(
        <>
            <input 
            placeholder = '할 일을 입력하세요.'
            value = {input}
            onChange = {onChange} />
        </>
    )       
}
```
3. 배열에 새 객체 추가하기
  * `id` 값은 `useState`로 처리해도 되지만, `useRef`를 사용하는 이유는 `id`값이 렌더링되는 정보가 아니며 단순히 객체 추가시에 참조되는 값이기때문에 굳이 `useState`쓰지 않았다.
  * `onSubmit event`는 `browser`를 강제로 새로고침 시킨다. 이를 방지하려면 `e.preventDefault()`를 넣자.
  * `onSubmit`은 `onClick`으로도 대체 가능하나 `Enter`키가 작동하지 않아 이 기능을 넣으려면 따로 `onKeyUp`으로 설정해줘야한다.
  * `onSubmit` 사용시 `button type='submit'`
```javascript
const App = () => {
    const [todo, setTodo] = useState([
      {
      id: 1,
      text: '고기 먹고싶다.',
      checked: true
      },
      {
      id: 2,
      text: '베라 먹고싶다.',
      checked: true
      },
      {
      id: 3,
      text: '롤 하고싶다.',
      checked: false
      },
    ])

    const nextId = useRef(4);
    const onInsert = useCallback(text => {
      const nextTodo = {
        id: nextId.current,
        text,
        checked: false
      }
    setInput(todo.concat(nextTodo))
    nextId.current += 1
    }, [todo])

    return(
        <>
          <TodoInsert onInsert = {onInsert}>
        </>
    )       
}
```
4. 버튼을 클릭하면 onSubmit 이벤트 발생하기
```javascript
const TodoInsert = ({onInsert}) => {
  const onSubmit = useCallback(e => {
    onInsert(input)
    setInput('')
    e.preventDefault()
  }, [onInsert, input])
  return(
    <form className="TodoInsert" onSubmit={onSubmit} />
  )}
```

---

### ⚡️ useCallback

```javascript
const memoizedCallback = useCallback(
  () => {
    doSomething(a, b);
  },
  [a, b],
);
```
`useMemo`와 비슷한 함수이며, 주로 렌더링 성능을 최적화해야 하는 상황에서 사용한다.
`useCallback`을 사용하면 만들어 놨던 함수를 재사용 할 수 있다.

예를들어, `onChange`와 `onInsert` 컴포넌트가 리렌더링 될 때마다 새로 만들어진 함수를 사용하게 된다.

대부분의 경우 이러한 방식은 문제가 없지만 <span style='color:blue'>컴포넌트의 렌더링이 자주 발생하거나 렌더링 해야 할 컴포넌트의 개수가 많아지면 이 부분을 최적화 해주는것이 중요</span>하다.

`useCallback`의 첫 번째 파라미터에는 생성하고 싶은 함수를 넣고, 두번 째 파라미터에는 배열을 넣으면 된다. 이 배열에는 어떤 값이 바뀌었을 때 함수를 새로 생성하는지 명시해야한다.

예를 들어, `onChange`처럼 비어 있는 배열을 넣게 되면 컴포넌트가 렌더링될 때 만들었던 함수를 계속해서 재사용하게 되며, `onInsert`처럼 배열 안에 `number`와 `list`를 넣게 되면 `input` 내용이 바뀌거나 새로운 항목이 추가 될때 새로 만들어진 함수를 사용하게 된다.

함수 내부에서 상태 값에 의존할때는 그 값을 반드시 두 번째 파라미터 안에 포함시켜 주어야 한다. 예를 들어 `onChange`의 경우 기존의 값을 조회하지 않고 바로 설정만 하기 때문에 빈 배열을 선언했지만, 

`onInsert`는 기존의 `number`와 `list`를 조회해서 `nextList`를 생성하기 때문에 배열 안에 `number`와 `list`를 꼭 넣어 줘야한다.

> reference: <a href='https://ko.reactjs.org/docs/hooks-reference.html#usecallback'>react official docs</a>

---

