# Scope

## def

- global scope
  - variable declared outside of all functions
- function scope
  - variable declared inside a function
- block scope
  - variable declared inside a block by `let` or `const`

## closures

### def

- "Closure is when a function is able to remember and access its lexical scope even when that function is executing outside its lexical scope."

### Pros

- encapsulation
- private data
- module


## Curry

- convert a function with multiple arguments into a sequence of functions with single argument

### Pros
- delay execution
- readable


## Hoisting

move declare, assign to the top of the scope during complietion

### can hoisting:
- function
- variable(let, const, var)

hoisting declare + assign:
- function
  - not include `var function`

hoisting declare(can't use before assign):
- let, const
  - `reference error`
- var
  - `undefined`

### can't hoisting:
- arrow function
- function expression
  ```javascript
  const a = function(){
    console.log('a')
  }
  ```

