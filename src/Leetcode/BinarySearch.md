# Binary Search


## General

```python
def find_insert_position(arr, target):
    l, r = 0, len(arr) - 1
    while l <= r:
        m = (l + r) // 2
        if arr[m] == target:
            return True
        elif arr[m] < target:
            l = m + 1
        else:
            r = m - 1
    return False 
```

在找不到值的时候, 会遇到2个情况:
1. 第一个大于target的, **插入位置**
   1. 返回L
2. 找小于等于target的最大值, 比如 `Search a 2D Matrix`在找row时
   1. 返回R
