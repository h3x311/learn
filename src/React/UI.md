# React UI

## button

```
<button type="button" className={isLike ? 'liked' : 'unliked'} 
onClick={()=>{
    setValue(itemValue)
}}>Primary</button>
```

## **hidden**

```
<div hidden={value}>
    <p>Hello</p>
</div>
```

## Hint

- 把参数放到组件外 传入


##  Form

form的每个item里包含`label`和`input`, 用div来wrap 每个item(label+input) label里的`for`和input的`id`一致(比如`username-input`).input里的属性比较多，重要的有`name`, `type`, **`required`**, `minlength`

### select - option

- `select` `option`
  - ```JSX
    <select value={value} onChange={(e)=>setValue(e.target.value)}>
      <option value="1">1</option>
      <option value="2">2</option>
      <option value="3">3</option>
    </select>
    ```

### FormData

```JavaScript
const formData = new FormData(event.target, event.nativeEvent.submitter);
const intent = formData.get('intent')
```

### Input

> 在JSX里不是`for`而是`htmlFor`
```JSX
<label htmlFor="input-box">Input</label>
```

```JavaScript
onKeyDown={(e)=>handleKeyDown(e)}
onPaste={(e)=>handlePaste(e)}
onFocus={(e)=>handleFocus(e)}
```

```JavaScript
function handleKeyDown(e){
    if(e.key === 'Enter'){
        // ex:`ArrowLeft` `Backspace` `Enter` `ArrowRight`
        console.log('enter')
    }
}
```
### Validation

- `inputMode='numeric'`
- `pattern='[0-9]*'`
  - `pattern="^[a-zA-Z0-9]+$"`
- `maxLength='10'`

### submit

submit里一定不要忘了`event.preventDefault()`

#### button

- submit中需要`disable input`
  - 哪些情况需要`disable`？

## Search input

在处理input时候可以用`toLowerCase()`和`trim()`来处理

- `placeholder`

```JSX
<input type="text" placeholder="Search..." />
```
### `textarea`


### Aria

- `aria-hidden`
- `aria-expanded`
- `aria-controls`
- `aria-label`
