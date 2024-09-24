# Array

## **iterated** item for **index** and **value**

```python
for index, value in enumerate(array):
    print(index, value)
```

## zip

```python
for a, b in zip(array1, array2):
    print(a, b)
```

## Sort

- intervals.sort(key=lambda x: x[0])
- will return NONE, change the original array

## deque

- appendleft
- insert(0, x)

## append or generate a array

```python
rows = [row[0] for row in matrix]
```