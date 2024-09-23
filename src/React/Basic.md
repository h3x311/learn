# React Theory

## preface

- component process
  - component(template) - instance - executed function - insert dom into Html(React use CreateElement)
  - component could manage its own state
    - one state one component, they are independent
- props 传递parent的state给child - external
  - newProps --> component re-render
- state 管理当前component的state - internal
  - state改变 --> re-render

## state management
- local state vs global state
  - local state: component instance
  - global state: context

| **条件**                                             | **结果**                                             |
|------------------------------------------------------|------------------------------------------------------|
| **需要存储数据**                                      |                                                      |
| 数据是否会在某个时间点发生变化？                      | 否 → 使用常规 `const` 变量                           |
|                                                      | 是 → 继续下一个条件                                  |
| 能否从现有的状态/props 计算出来？                      | 是 → 派生状态（`Derive state`）                      |
|                                                      | 否 → 继续下一个条件                                  |
| 它是否应该重新渲染组件？                              | 否 → 使用 `Ref`（`useRef`）                          |
|                                                      | 是 → 在组件中创建一个新的状态                        |
| **何时创建状态**                                      | **何处放置状态**                                     |
| 该状态是否仅由当前组件使用？                          | 是 → 将状态保留在组件中                              |
|                                                      | 否 → 继续下一个条件                                  |
| 该状态是否也被子组件使用？                            | 是 → 通过 props 传递给子组件                         |
|                                                      | 否 → 继续下一个条件                                  |
| 该状态是否被一个或几个兄弟组件使用？                  | 是 → 将状态提升到第一个共同的父组件                 |
|                                                      |                                                      |

## Render Process
React to state changes by re-render UI😂

### 2 conditions to re-render
- initial render
- state update - component re-render - view re-render
> **Virtual DOM **- cheap and fast to create multiple trees. Caused write to dom is expensive and slow, usually only small part need to update


### Render phase
Has impact on all of its children
- **Reconciler** - decide which DOM elements need to update
  - fiber tree(fiber for each component and DOM element)
    - contain: state, props, side effects, hooks, queue of work...
- Updated React Elements --> new Virtual DOM + current Fiber Tree --> reconciliation + diff
- render(diff) > patch(diff) > re-render
- **Asynchronous**(Can be splited into diff chunks)
  - render will not been triggered instantly, but will be scheduled when JS engine is idle 


### Commit phase
- **list** of DOM updates --> **Renderers**(ex: ReactDOM): write to dom --> update UI
- commit is **synchronous**
- after finish commit, WIP fiber tree become current fiber tree

#### diff
- same position, different element
  - **destroy** old tree including its children
- same position, same element
  - **更新属性**,不重新渲染DOM(element and state)

### browser paint








## Component Instance Lifecycle

- Mounting(initial render)
- Updating(state/props/parent rerenders/context update)
- Unmounting(remove component)
![4pc0dQtest](https://cdn.jsdelivr.net/gh/h3x311/upic@main/LC3/2024/4pc0dQtest.png)