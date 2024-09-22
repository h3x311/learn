# Interval

## Preface
分Insert和Merge
## Merge
先排序`intervals.sort(key=lambda x: x[0])`,再iterate.

iterate时候有两种情况，有没有`overlap`(curr[0] <= prev[1])，如果有overlap的话，prev更新为新的interval，首min尾max。没有的话，更新prev为curr。

> Hint: Edge->需要append最后一个interval。

关于排序，如果不需要考虑`更新中间值`的话(比如Minimum Number of Arrows to Burst Balloons)，可以用`intervals.sort(key=lambda x: x[1])`，如果需要考虑`更新中间值`的话(比如Merge Intervals)，可以用`intervals.sort(key=lambda x: x[0])`。

## Insert
- 先append 无overlap（end < newInterval[0]）
- 再append 有overlap (start <= prev[1])
- 再append 无overlap（把剩下的append）

用while 来控制each循环。

