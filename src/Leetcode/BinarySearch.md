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

## overflow 

use `l + (r - l) // 2` to avoid overflow

## rotation of array

rotate array的二分搜索比较困难,因为判断的条件比较难思考.

- 首先判断m在哪段
  - 根据nums[m] 和nums[r]的比较
- 如果是target的话,再判断是在m的左边还是右边
  - 根据是否满足固定区间来划分
- 如果是最小值的话 返回l
- 注意边界条件(不要越界 `0<x<len(nums)-1`)



## time complexity/space complexity

`O(log n), O(1)`