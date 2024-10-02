# QA
## Transition
- duration
# CSS Basic
## 命名

- `wrapper`
- `container`
- `flex-container`
- `input-box`


## pseudo class

- `first-child`
- `:not(:first-child)`
### Hover

```css
.btn:hover {
    background-color: red;
}
```

## def variable and use

```css
:root {
    --blue: #007bff;
}

.btn {
    background-color: var(--blue);
}
```


## button

### name
- `button--primary`
- `button--secondary`
- `button--danger`


```css
.btn {
    cursor: pointer;
    padding: 4px 8px;
    font-weight: bold;
    align-items: center;
    border: 1px solid #000;
    border-radius: 2rem;
    display: flex;
    gap: 1/2rem;
}
.btn:focus{
    outline: 2px solid #000;
  outline-offset: 1px;
}
.btn:disabled{
    opacity: 0.25;
    cursor: not-allowed;
    transition: all 0.3s linear;
}
```

## input

```css
input:focus {
    outline: 1px solid #000;
}

```css
.input-box {
  --size: 3rem;
  height: var(--size);
  width: var(--size);
  border: none;
  outline: none;
  font-weight: 600;
  font-size: 1.5rem;
}

```

```
## hidden

```css
.hidden {
    display: none;
}
```

## wrapper

```css
.wrapper {
    width: 100vw;
    height: 100vh;
}
```
## BEM

> 先说细节,再说更加specific的

EX: `like-button--default` 和 `like-button--liked`