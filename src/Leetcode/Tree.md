# Tree

## BFS

- declare a queue
```python
queue = deque([root])
```
- pop from queue`popleft`
```python
node = queue.popleft()
```

## DFS
最简单的，base case+recursion on chilren

稍微复杂一点，加help function，在help function里recursion

## recursion

`Construct Binary Tree from Preorder and Inorder Traversal`这个题目很巧妙，第一次想不出来办法的那种，貌似有点想出来，但还是看答案才恍然大悟。通过root来分array，递归的建立左右子树。

## Binary Search Tree
基本是需要inorder的遍历,需要helper函数.
- 在helper函数外声明全局变量(1个是result,1个是prev,都声明为`None`)
- help函数
  - 首先判断是否有node和res是否不是None,是的话就返回
  - 递归左子树
  - 如果prev不是None,就更新result和prev
  - 更新prev
  - 递归右子树
- 调用helper函数
- return res

### example
```python
class Solution:
    def isValidBST(self, root: Optional[TreeNode]) -> bool:
        self.isbst = None
        self.prev = None
        def dfs(node):
            if not node or self.isbst is not None:
                return
            dfs(node.left)
            if self.prev is not None:
                if self.prev >= node.val:
                    self.isbst = False
                    return
            self.prev = node.val
            dfs(node.right)
        dfs(root)
        return True if self.isbst == None else False
```

### time complexity/space complexity
`O(N), O(logN)-O(N)`