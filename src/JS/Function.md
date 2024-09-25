# Function

## this
- global
  - window
  - `undefined` in strict mode
- function call on object
  - `this` is the object 
- constructor func
  - new instance object
- arrow function
  - `this` is the surrounding scope
- call, apply, bind
  - `this` is the first argument


## Arrow function

- no `this`
  - scope: surrounding scope
- can't be used as constructor
- no `arguments`

## call, apply, bind

- `call`: use rest parameters
- `apply`: array
- `bind`: return a new function 



## IIFE
- make a new scope in case of polluting global namespace




## IIFE(Immediately invoked function expression)

```Javascript
(()=>{

})()
```
