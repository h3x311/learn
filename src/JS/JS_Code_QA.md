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