# Array
## Table of Contents

- [Array](#array)
  - [Table of Contents](#table-of-contents)
  - [reduce](#reduce)
  - [Init methods](#init-methods)
  - [Copy Array Clone](#copy-array-clone)
    - [Not change original array - Shallow Copy](#not-change-original-array---shallow-copy)
    - [change original array](#change-original-array)
    - [Deep Copy](#deep-copy)
  - [Methods](#methods)
    - [return new array](#return-new-array)
  - [change original array](#change-original-array-1)

## reduce

reduce is a simplified version of iteration
```JS
arr.reduce((acc, cur) → acc + cur.price, 0);
```

## Init methods

- `[]`
- `new Array()`
- `Array.of(1, 2, 3)`
- `Array.from({ length: 3 }, (_, i) => i)`
- `Array.from(set)`
- `Array(3).fill('x')`
  - 初始化包含x个为y元素的array

## Copy Array Clone

### Not change original array - Shallow Copy

- **`arr.slice()`**
- `arr.concat()`

### change original array
- `[...arr]`

### Deep Copy

- `JSON.parse(JSON.stringify(arr))`
- `Array.from(arr)`

## Methods

### return new array

- `arr.map(fn)`
- `arr.filter(fn)`
- `arr.reduce(fn, initialValue)`
- `arr.flat(depth)`
- `arr.flatMap(fn)`
- `arr.slice(start, end)`
  - start: 开始索引
  - end: 结束索引(不包括)

- `arr.every(fn)`
- `arr.some(fn)`
- `arr.find(fn)`
- `arr.findIndex(fn)`
- `arr.indexOf(item)`
- `arr.lastIndexOf(item)`
- `arr.includes(item)`

## change original array

- `arr.splice(start, deleteCount, item1, item2, item3)`
  - deleteCount: 删除的元素个数
  - item1, item2, item3: 添加的元素
  - 主要是删除元素，添加元素
- `arr.push(item)`
- `arr.pop()`
- `arr.shift()`
- `arr.unshift(item)`
- `arr.reverse()`
- `arr.sort(fn)`
- `arr.sort((a, b) => a - b)`
