# string methods

## Combine 2 strings to hashmap

```python
zip(s1, s2)
input: s1 = "abc", s2 = "xyz"
output: [('a', 'x'), ('b', 'y'), ('c', 'z')]
```

## the 1st char index of string

```python
strs.index('h')
input: strs = "hello"
output: 0
```

## split string to list

```python
strs.split()
input: strs = "hello world"
output: ['hello', 'world']
strs.split('/')
input: strs = "hello/world"
output: ['hello', 'world']
```
> it can split by any character, by default is space

## Count the char in string

```python
str_count = collections.Counter(strs)
```

## 判断字符串的condition
- startswith
  - ```python
    "hello".startswith("h")
    ```
- endswith
  - ```python
    "hello".endswith("o")
    ```

## iterate string

- 不需要用range，可以用slice
```python
for string in strs[1:]:
    if string.startswith(strs[0]):
        continue
    else:
        return False
return True
```

## reverse string
- 用slice, 返回新的list
```python
strs = strs[::-1]
```
- 用reverse，返回None
```python
strs = list(strs)
strs.reverse()
strs = "".join(strs)
```

## remove space
- strip
```python
"  hello  ".strip()
```
- lstrip
```python
"  hello  ".lstrip()
```

## split string to list
- split
```python
"hello world".split()
```

## join list to string
- join
```python
" ".join(["hello", "world"])
```

## replace
- replace
```python
"hello world".replace("world", "python")
```

## lower and upper
```python
"HELLO WORLD".lower()
"hello world".upper()
```
