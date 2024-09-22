# Type Comparison

在GFE做了很多type相关的题目，比如`deep equal`，重点type是`Object`和`Array`,先遍历，如果item是多层嵌套的，在每个item递归调用，另外，在`Object`中，还需要排除`null`的情况。

> Hint: `forEach`里的`return`不会终止循环，`for`里的`return`会终止循环。其他的思路是，可以用every和some，他们可以中止循环。

## `Primitive`

- `Object.is(NaN, NaN)`
- `typeof NaN`
- `Object.prototype.toString.call(valueA)`


## `Object`

首先判断是不是object，可以用typeof和判断不是null。

通过`Object.keys()`来拿到keys，先判断length是否一致，再用`for...of`来遍历，递归调用`deepEqual`。

### 判断object
- ` Object.getPrototypeOf(value) === Object.prototype`
- `value instanceof Object`
- `typeof value === 'object' && value !== null`

### iterate object


### 判断obj里有没有x属性

- `Object.hasOwn(obj, x)`
- `Object.prototype.hasOwnProperty.call(obj, x)`


## `Array`

思路的是先判断是否是array，再判断length是否一致，再遍历，遍历时候递归来判断每个item是否一致.注意`forEach`里的`return`不会终止循环，`for`里的`return`会终止循环。

