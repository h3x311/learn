# DOM
## definition
- Allows us to make JavaScript interact with the browser;
- We can write JavaScript to create, modify and delete HTML elements; set styles, classes and attributes; and listen and respond to events;
- DOM tree is generated from an HTML document, which we can then interact with;
- DOM is a very complex API(Application Programming Interface) that contains lots of methods and properties to interact with the DOM tree
![KKharntest](https://cdn.jsdelivr.net/gh/h3x311/upic@main/LC3/2024/KKharntest.png)

## select element
- 

## event

## Form process
- 用`querySelector`来获取form
- 


## select element

```JavaScript
console.log(document.documentElement)
console.log(document.head)
console.log(document.body)

document.querySelector('form')
const $form = document.querySelector('form')
// select id
const $usernameInput = document.querySelector('#username-input')
// select class
const $usernameInput = document.querySelector('.username-input')
// select tag
const $usernameInput = document.querySelector('input')
// select tag
const allInputs = document.getElementsByTagName('input')
// select class
const allInputs = document.getElementsByClassName('username-input')
// select id
const $usernameInput = document.getElementById('username-input')
```
## create element

```JavaScript
const $newInput = document.createElement('input')
$newInput.classList.add('new-input')
$newInput.innerHTML = 'New Input'
```
## position insert element

- append, prepend, before, after

## delete element
```JavaScript
$newInput.remove()
```

## set Attribute

```JavaScript
$usernameInput.removeAttribute('minlength')
$usernameInput.setAttribute('minlength', '4')
```

## CSS add class

```JavaScript
$usernameInput.classList.add('hidden')
$usernameInput.classList.remove('hidden')
```

## FormData

> formData.get(name)里的parameter对应的是input的name

```JavaScript
const formData = new FormData($form)
const username = formData.get('username')
```

## Event Listener

```JavaScript
$form.addEventListener('submit', async (event) => {
  event.preventDefault()
})
```


