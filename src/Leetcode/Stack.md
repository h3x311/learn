# Stack

如果是字符串的话，可以用split转换为array再遍历

Generally，是需要先遍历（考虑遍历的顺序），然后在某种情况下pop和append。
所以关键是如何找到相应的condition。有时候需要跟stack的peek(stack[-1])做比较