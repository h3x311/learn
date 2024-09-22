# Slide Window

找子集

## base condition
先考虑总string和target string的base条件

# general process
固定左边的指针，iterate 右边的指针（edge 不要越界

移动时计算**process value**，看是否满足condition，满足的话，就更新res值，移动左指针（寻找更优解，需要reset 右指针），移动前需要update **process value**(依赖于指针，所以需要在移动前更新)，不满足的话，就移动右边的指针

关键点在于如何找到**process value**和condition

像minimum size subarray sum，比较简单,因为需要的是子集的`结果值`，而不是`过程值`.

像longest substring without repeating characters，对过程值的要求是norepeat，所以需要在遇到重复字符时，把left指针移到上个重复字符的下一个位置。所以需要在**process value** 里存字符的index和字符本身，用hashmap

像substring with concatenate words 和 Minimum Window Substring，要求permute，所以最好是用curr代表已经满足的unit，把left 移动到第1个word之后 （还需要check 多余的wordm,因为要求是unique）当和总共的unit相等时候，就可以append，如果不满足的话，就把l移动到r？ 所以需要把**process value**存到hashmap里，在遍历的时候不断的去trim这个window多余的key 的值

