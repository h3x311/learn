# Matrix

最简单的是遍历存值，根据process value来二次遍历替换
比如说valid sudoku, set matrix zero

一般来说，需要初始化left和right的boundary。
比如说 Rotate Image，确定boundary，在boundary之间iterate,再根据order来遍历不同的方向

Spiral Matrix也是类似的

Game of Life 这个题的话，有点像island，主要是分开，先算neighbor，再映射结果，再反映射，难点在于算neighbor那里，可以用区间来n2 iterate，而不是手工的调用八个方向

