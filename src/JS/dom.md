# DOM

## Form process
- 用`querySelector`来获取form
- 


## get Element

```JavaScript
const $form = document.querySelector('form')
const $usernameInput = document.querySelector('#username-input')
const $usernameInput = document.getElementById('username-input')
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


