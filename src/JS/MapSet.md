# Map

## Initialize

```js
const map = new Map([
  ['key1', 'value1'],
  ['key2', 'value2'],
]);
```

## Methods

- `map.set(key, value)`
- `map.get(key)`

- `map.has(key)`
- `map.delete(key)`
- `map.clear()`
- `map.size`

## Iteration

```js
for (const [key, value] of map) {
  console.log(key, value);
}
```

# Set

## Initialize

```js
const set = new Set([1, 2, 3]);
```

## Methods

- `set.add(value)`
- `set.has(value)`
- `set.delete(value)`
- `set.clear()`
- `set.size`

## Iteration

```js
for (const value of set) {
  console.log(value);
}
```