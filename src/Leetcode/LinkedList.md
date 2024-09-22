# Linked List

## Basic

### Base condition

```python
if not head:
    return None
```

如果是结构上的操作的话，比如rotate或者reverse，需要的base condition会多一点：
```python
if not head or not head.next or k == 0:
    return head
```

> Hint: rotate结束的时候，注意要break，不然会有cycle，最后end节点point to `None`

### dummy node

> 为了处理边界情况，比如删除头结点，或者反转链表。

```python
dummy = ListNode(0, head)
```
## Init Node

```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next
# example 
dummy = ListNode()
curr = dummy
curr.next = ListNode(1)
# move curr to next 
curr = curr.next
return dummy.next
```
## Reverse
### Reverse Part of List

思路的是，先遍历到part之前，记录part的first node（reverse后的last node），遍历这个part并且reverse，再把part的终点指向之后那段的头。

步骤的话比较detail，
首先create一个dummy node，指向当前的head，返回的时候用`dummy.next`即可。
遍历到part前，是left-1个，用`range(left-1)`, 把prevLeft和curr迭代向后

之后是reverse的部分，用`range(right-left+1)`。prev指向null。
```python
temp = curr.next
curr.next = prev
prev, curr = curr, temp
```
最后，连接这3部分，leftprev.next仍指向part的first node，所以 part里的最后一个node是`leftprev.next`

- prevLeft的最后一个node: prevLeft `2. prevLeft.next = prev`
- part里的最后一个node： prevLeft.next （没有删除的link）`1. prevLeft.next.next = curr`
- part里的第一个node: prev （遍历的最后一轮）
- prevRight的第一个node: curr （遍历的最后一轮）

### Reverse 之头插法

<!-- WIP TODO -->

## Hashmap + Linked List

### Copy List with Random Pointer

把node的val放到hashmap里，再遍历linklist。把next和random的link建立起来。所以说是用hashmap建立了node和copynode的映射关系，可以在二次遍历的时候填充其他的link。

### LRU
双向链表，并且每个node有key，value,存放在hashmap里.

双向链表的初始化: 
```python
self.left.next = self.right
self.right.prev = self.left
```
先初始化一个Node Class. get操作简单，在hashmap里找item，并且更新下存储的顺序，用到了基础的操作insert和remove。先remove再insert。put的话，需要删除当前key对应的node，并且check capcity，如果满了就`remove`最前面的node，insert新的node。

关于insert 和 remove，insert需要在链表的尾部，做指针的更新。remove需要找到node后，更新前后的link。


