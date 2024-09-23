# Graph

## Topological Sort

> 主要是查找DAG(有向无环图)的拓扑排序
- 存indegree `child -> indegree`
- 存child -> hashmap: `parent -> [child, child]`
- 将indegree为0的node加入 `deque`
- 从deque中pop node到stack，将child的indegree减1，如果child的indegree为0，则将child加入deque
- 最后stack中的node就是拓扑排序的结果

## Island

- init `visited` to `set()`
- 遍历grid(两层)
- 如果是`1`, 并且没在`visited`中, 岛屿数量加1, 则`dfs`
- dfs里判断在grid的range里,并且是1,没被visited,不符合范围,直接返回
- 否则,添加到visited里并且把`dfs`的四个方向都走一遍

## Clone Graph

### DFS

- 用hashmap 来存original和clone的关系
- base condition: 如果node是None, 返回None

Helper function:
- 如果node在hashmap中, 返回clone的node
- 否则，create clone node, 存入hashmap
- 遍历node的neighbors, 递归调用dfs, 将结果加入clone的neighbors
- 返回clone node

### BFS
- 用deque来存node
- 遍历deque, 将curr从deque中popleft出来
- 遍历curr的neighbors, 如果没被访问过, 将neighbors加入deque, 并且加到visited里
- 把`visited[neighbor]` append到`hashmap[curr].neighbors`里
- 返回clone node
