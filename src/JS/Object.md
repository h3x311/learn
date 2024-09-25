# Object

## Prototype

- Get prototype
  - `__proto__`
  - `Object.getPrototypeOf(obj)`
- Set prototype
  - `Object.setPrototypeOf(obj, proto)`

## Create object

- `{}`
- `new Object()`
- `Object.create(proto)`
- constructor function
- class

## Basic method
- `Object.values(obj)`
- `Object.keys(obj)`
- `Object.entries(obj)`
- `Object.fromEntries(iterable)`
- `Object.hasOwn(obj, key)`
  - filter inherienced properties
- Object.getOwnPropertyNames(obj)
  - return an array of all properties (including non-enumerable properties) found directly upon a given object.


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