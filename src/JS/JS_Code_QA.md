# JS_Code_QA
## Debounce
先用clearTimeout清理上一个timeoutId, setTimeout后, 再执行函数
```JavaScript
export default function debounce(func, wait=0) {
    // clear timeid
  let timeoutId = null
  return function(...args){
    // store this 
    const context = this
    clearTimeout(timeoutId)
    // store timeid 
    timeoutId = setTimeout(function(){
      timeoutId = null // not necessary but good to have
      func.call(context, ...args)
    },
    wait)
  }
}
```

## Throttle

判断是否在throttle状态, 如果是, 则不执行函数, 否则先打开, 再执行函数, 执行完了, timeout后再关闭throttle

```JavaScript
export default function throttle(func, wait = 0) {
  let shouldThrottle = false;

  return function (...args) {
    if (shouldThrottle) {
      return;
    }

    shouldThrottle = true;
    setTimeout(function () {
      shouldThrottle = false;
    }, wait);
    // 先执行函数, 执行完了再把throttle打开
    func.apply(this, args);
  };
}
```

## Array.prototype.filter

```JavaScript
Array.prototype.myFilter = function (callbackFn, thisArg) {
  const len = this.length;
  const results = [];

  for (let k = 0; k < len; k++) {
    const kValue = this[k];
    if (
      // Ignore index if value is not defined for index (e.g. in sparse arrays).
      Object.hasOwn(this, k) &&
      callbackFn.call(thisArg, kValue, k, this)
    ) {
      results.push(kValue);
    }
  }

  return results;
};
```

## Promise.all

```JavaScript
export default function promiseAll(iterable) {
  return new Promise((resolve, reject) => {
    const results = new Array(iterable.length);
    let unresolved = iterable.length;

    if (unresolved === 0) {
      resolve(results);
      return;
    }

    iterable.forEach(async (item, index) => {
      try {
        const value = await item;
        results[index] = value;
        unresolved -= 1;

        if (unresolved === 0) {
          resolve(results);
        }
      } catch (err) {
        reject(err);
      }
    });
  });
}
```

## Curry(Closure)

```JavaScript
export default function curry(func) {
  return function curried(...args) {
    if (args.length >= func.length) {
      return func.call(this, ...args);
    }

    return (arg) =>
      arg === undefined
        ? curried.call(this, ...args)
        : curried.call(this, ...args, arg);
  };
}
```

## Flatten

### Iterative
```JavaScript
export default function flatten(value: Array<ArrayValue>): Array<any> {
  const res = [];
  const copy = value.slice();

  while (copy.length) {
    const item = copy.shift();
    if (Array.isArray(item)) {
      copy.unshift(...item);
    } else {
      res.push(item);
    }
  }
  return res;
}
```
### Iterative with `some`
```JavaScript
export default function flatten(value: Array<ArrayValue>): Array<any> {
  while (value.some(Array.isArray)) {
    value = [].concat(...value);
  }

  return value;
}
```

### Recursive(risk overflowing the call stack)
```JavaScript
export default function flatten(value) {
  return value.reduce(
    (acc, curr) => acc.concat(Array.isArray(curr) ? flatten(curr) : curr),
    [],
  );
}
```

### flat array in place(mutate array)
```JavaScript
export default function flatten(value: Array<ArrayValue>): Array<any> {
  for (let i = 0; i < value.length; ) {
    if (Array.isArray(value[i])) {
      value.splice(i, 1, ...value[i]);
    } else {
      i++;
    }
  }

  return value;
}
```

### Recursive `flatMap`
```JavaScript
export default function flatten(value: Array<ArrayValue>): Array<any> {
  return Array.isArray(value) ? value.flatMap((item) => flatten(item)) : value;
}
```

### Generator
```JavaScript
export default function* flatten(value: Array<any>): Array<any> {
  for (const item of value) {
    if (Array.isArray(item)) {
      yield* flatten(item);
    } else {
      yield item;
    }
  }
}
```

## mutate array
pop, push, reverse, shift, sort, splice, unshift, copyWithin and fill.

## getElementsByClassName
```JavaScript
function isSubset(a, b) {
  return Array.from(a).every((value) => b.contains(value));
}

export default function getElementsByClassName(element, classNames) {
  const elements = [];
  const classNamesSet = new Set(classNames.trim().split(/\s+/));

  function traverse(el) {
    if (el == null) {
      return;
    }

    if (isSubset(classNamesSet, el.classList)) {
      elements.push(el);
    }

    for (const child of el.children) {
      traverse(child);
    }
  }

  for (const child of element.children) {
    traverse(child);
  }

  return elements;
}
```
## Deep Clone
```JavaScript
export default function deepClone(value) {
  if (typeof value !== 'object' || value === null) {
    return value;
  }

  if (Array.isArray(value)) {
    return value.map((item) => deepClone(item));
  }

  return Object.fromEntries(
    Object.entries(value).map(([key, value]) => [key, deepClone(value)]),
  );
}
```