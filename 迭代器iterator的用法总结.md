<font size="6">迭代器iterator的用法总结</font>

[TOC]

# 概念

可以简单理解成**指针**
定义：

```cpp
container<type>::iterator it;
```
# 分类

可以分成**输入迭代器、输出迭代器、前向迭代器、双向迭代器、随机访问迭代器**
这里只介绍使用较多的**双向迭代器**和**随机访问迭代器**
双向迭代器和随机访问迭代器都可以进行 ++、--、==、!= 的运算，但随机访问迭代器还可以进行<、>、+=x、-=x 的运算
**举个栗子**
遍历容器时，双向迭代器和随机访问迭代器都可以使用
```cpp
for (it = v.begin(); it != v.end(); it ++ )
```
只有随机访问迭代器可以使用
```cpp
for (it = v.begin(); it < v.end(); it ++ )
for (it = v.begin(); it < v.end(); it += 1 )
```
且只有随机访问迭代器支持下标运算符，也就是把数据容器当做数组这种表示方式（e.g. a[3]）

- 随机访问迭代器：vector、deque
- 双向迭代器：set / multiset、list、map / multimap
- 不支持迭代器：stack、queue

# 辅助函数
## advance（it， n）
将迭代器 it 向后移动 n 位（n 可以是负数）
## distance（it~1~， it~2~）
输出it~1~、it~2~之间的距离
## iter_swap（it~1~,  it~2~）
交换it~1~、it~2~指向的值

# 特殊的迭代器
## begin() 和 end()
返回 iterator
**begin()：**返回一个指向容器第一个元素位置的指针
**end()：**返回一个指向容器最后一个元素后一个位置的指针
可以利用 *(container.begin()) 来修改容器中的元素
## cbegin() 和 cend()
返回 const_iterator
**cbegin()：**返回一个指向容器第一个元素位置的指针
**cend()：**返回一个指向容器最后一个元素后一个位置的指针
const **不**可以利用 *(container.cbegin()) 来修改容器中的元素
## rbegin() 和 rend()
逆序迭代器 返回 iterator
**rbegin()：**返回一个指向容器最后一个元素位置的指针
**rend()：**返回一个指向容器第一个元素前一个位置的指针
可以利用 *(container.rbegin()) 来修改容器中的元素
## crbegin() 和 crend()
const 修饰的逆序迭代器 返回 const_iterator
**crbegin()：**返回一个指向容器最后一个元素位置的指针
**crend()：**返回一个指向容器第一个元素前一个位置的指针
const **不**可以利用 *(container.crbegin()) 来修改容器中的元素