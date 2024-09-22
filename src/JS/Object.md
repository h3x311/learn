# Object

## Basic method
- `Object.values`


## 判断key是否是原生的

```js
Object.hasOwn(obj, key)
```

## iterate object

```js
for (const [key, value] of Object.entries(obj)) {
    console.log(key, value);
}
Object.entries(obj).map(([key, value]) => {
    console.log(key, value);
})
```

## 判断是否是object

- `typeof obj === 'object' && obj !== null`
  - 不能判断`obj`是`Array`，`Function`等。
- isPlainObject 判断是否是纯对象，排除`Array`，`Function`等。

```js
function isPlainObject(value) {
  if (value == null) {
    return false;
  }

  const prototype = Object.getPrototypeOf(value);
  return prototype === null || prototype === Object.prototype;
}
```