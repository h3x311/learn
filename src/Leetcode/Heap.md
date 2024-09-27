# Heap

## basic operation

- `import heapq`
- push `heapq.heappush(heap, item)`
- pop `heapq.heappop(heap)`

## pattern

- store all items in array(max need to start -x)
- then pop within k times to find max kth or min kth

重点是搞明白heap需要按照什么key来排序,再搞明白如何push进heap的order(如何优化时间复杂度)