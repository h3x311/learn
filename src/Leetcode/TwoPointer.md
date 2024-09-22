# Two Pointer

## two pointer
一般针对**排序**过的数组，去找target的pair

最简单的模式(比如：Two Sum II - Input Array Is Sorted)：
- 初始化两个指针，一头一尾
- 如果大于，左移动r pointer
- 如果小于，右移动l pointer
- 如果相等，返回

第二种模式是两个数组，思路：

两个一起遍历，在某种情况下移动左边，某种情况下移动右边

有一个很大的细节是需要考虑在遍历的过程中有时候需要**skip**，一般是用while，condition时需要判断pointer是否越界，并且是否满足特定的condition。比如valid Palindrome。

另一个例子是3 sum，在每个指针移动时都需判断是否跟上一个值相同，如果相同，需要继续Skip，直到不相同为止。

总之，难点是找**左右指针移动的条件**。比如Container With Most Water，移动的条件是移动height小的pointer来找更大的面积
## Merge Two Sorted Lists
跟array的没啥区别

### Add Two Numbers
这个需要两个指针，iterate这两个linklist，并且存extra进位的值，没有的后就是0，更新进位。移动指针直到None。

## slow and fast pointer

这个还有点难思考出来。
删除第n个节点，用两个指针，fast先走n步，然后slow和fast一起走，直到fast到结尾，此时slow的下一个节点就是要删除的节点。