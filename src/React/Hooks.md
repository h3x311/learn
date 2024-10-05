# Hooks


## `useState`

### 多个相同的组件的state

可以用`set`来管理

### update state

- 函数式更新(可以拿到上一次的state)
```JSX
setStep((prev)=>prev+1)
```

```JSX
// closure
set((prev)=>
prev.map((item)=>item.id === 1 ? updatedItem: item)
)
```

### Initial State

- 如果是obj的arr，可以加一个id属性，方便CRUD
- 不知道用啥,可以选择`null`

```JSX
const generateId = (() => {
  let id = 0;
  return () => `${id++}`;
})();
```

## `useEffect`
> side effect, like the event handler, but it needs to be triggered by event, useEffect is more flexible
> Need a clean up function?
### points
- Effect is sync, so the async func need to be wrapped in another func
- useEffect could be called twice in `React Strict Mode`, not in `production`
- 在调api前后加loading state
- 用try catch, 在catch里setError,在return里render <Loading> or <Data> or <Error>
- the code don't need to run every re-render
- it could be executed on every render stage, depending on dependency array

### Dependency Array
- []
  - init render(mount)
- [state, props]
  - init render(mount)
  - state or props change
- no dependency array
  - run on every render

### Clean Up
- 在effect前和unmount后执行



## `useRef`

> 返回一个可变的 ref 对象，其 `current` 属性被初始化为传入的参数（initial value）。返回的 ref 对象在组件的整个生命周期内保持不变。

- `const inputRef = useRef<HTMLInputElement>([]);`
- Input
  - `ref={(el) => inputRef.current = el}`
- focus
  - `inputRef.current[index].focus()`

- Creating a variable that stays the same between renders (e.g. previous state, setTimeout id, etc.)
- Selecting and storing DOM elements
- Refs are for data that is NOT rendered: usually only appear in event handlers or effects, not in JSX (otherwise use state)
![6euXnltest](https://cdn.jsdelivr.net/gh/h3x311/upic@main/LC3/2024/6euXnltest.png)

## useContext
- provider: given children access to context value
- value: context value
- useContext: consume context value

value updated -> consumers re-render

## useReducer
![jq9Vyqtest](https://cdn.jsdelivr.net/gh/h3x311/upic@main/LC3/2024/jq9Vyqtest.png)

## Redux

- used in lots of UI state global management