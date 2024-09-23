# Hashmap

## Preface
总体不难，一般是先存值，遍历，看是否满足特定的condition。

## Basic

```python
# 初始化
hashmap = {}
# 存值
hashmap[key] = value
# 取值
value = hashmap.get(key, default_value)
# 删除
del hashmap[key]
```

## Iteration

```python
for key, value in hashmap.items():
    print(key, value)
for key in hashmap:
    print(key)
for value in hashmap.values():
    print(value)
```

## data type
重点是如何存值，可能涉及到从str --> list --> str的转换(list(str))，比如把一个str重新排序，比如group anagram
还需要考虑对input的预处理，如果重复char没有意义，先用Set来去重，再开始iterate

如果只有数量的维度的话，比较简单，存值和看是否满足condition就可以

## 2 arrary
如果有2个Array，先存第1个hashmap，在遍历第2个array的时候，来对第1个hashmap进行反作用的镜像操作, 比如Ransom Note

## two array map relation
如果有map的关系，思路是把2个arr用zip bound在一起，遍历的时候，判断map的值是否是另个arr的value，不存在的话加入map，对方也是相同的操作。比如`Isomorphic Strings和word Pattern`




