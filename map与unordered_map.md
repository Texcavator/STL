<font size="6">map 与 unordered_map</font>

[TOC]

# map

一对一的 key - value 键值对
- key：关键字
- value：关键字的值

**==内部自动排序==**
内部实现一个红黑树（非平衡二叉搜索树）

## 声明

**头文件：**
```cpp
#include <map>
```
**定义：**
```cpp
map<int, string> Name;
```
意为定义了一个 int 指向 string 的名为 Name 的 map
# unordered_map
- key：关键字
- value：关键字的值

内部实现一个哈希表
## 声明
**头文件：**
```cpp
#include <unordered_map>
```
**定义：**
```cpp
unordered_map<int, string> Name;
```
意为定义了一个 int 指向 string 的名为 Name 的 unordered_map
# 常用函数
## 增加元素
1. **下标插入**
举个栗子
```cpp
map<int, string> mymap;
mymap[5] = "haha";
```
如果map[5]本来就有值，替换原有值，如果本来不存在，则创建该元素

2. **insert()**
以 map<int, string> mymap 为例
- 插入单个值
```cpp
mymap.insert(pair<int, string>(1, "aa"));
```
- 插入单个值至指定位置
```cpp
map<int, string>::iterator it = mymap.begin();
mymap.insert(it, pair<int, string>(1, "bb"));
```
- 插入多个值至指定位置
```cpp
map<int, string> othermap;
othermap.insert(mymap.begin(), mymap.find(2));
```
## 删除元素
1. **clear()**
清空map中的元素
2. **erase()**
举例说明
- 传入迭代器，删除该位置元素，返回下一位置迭代器
```cpp
map<int, string>::iterator it = mymap.begin();
map<int, string>::iterator ita;
ita = mymap.erase(it);
```
- 传入两端迭代器，删除区间内元素，返回下一位置迭代器
```cpp
map<int, string>::iterator ita = mymap.begin();
map<int, string>::iterator itb = mymap.end();
map<int, string>::iterator itc;
itc = mymap.erase(ita, itb);
```
- 传入 key，删除 key 指向的元素，返回删除元素个数
```cpp
int size = erase(key);
```
## 取值
1. **下标取值**
```cpp
string s = mymap[3];
```
如果该位置原本没有值也不会报错
2.  **at**
```cpp
string s = mymap.at(2);
```
如果该位置原本没有值会报错
## 其他常用函数
1. **empty()**
返回容器是否为空
2. **size()**
返回容器中键值对的数量
3. **count(key)**
返回 key 对应的元素个数
4. **swap(map)**
交换两个map的元素
5. **find(key)** 
找到就返回该元素的迭代器
找不到就返回end()
6. **==**
只有 key 和 value 全都相等时，== 才成立
# map 与 unordered_map 的区别
- map 最大的特点就是排序，因此遇到排序的情况可以选用 map
- unordered_map 由于使用哈希表存储，查找效率非常高，复杂度可以达到 O(1)