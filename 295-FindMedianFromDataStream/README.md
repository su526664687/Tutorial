## 题目分析：

设计一个数据结构，支持1) 从数据流中添加一个整数到数据结构中; 2) 返回到目前为止的所有元素的中位数。

### 解题思路（1）
题号480的simple版，无删除操作。每次查询暴力排序。很遗憾，会超时。
### 解题思路（2）
维护两个堆，一个保存前一半的数，另一个保存后一半的数，我们就能轻易求得中位数。单次操作的复杂度为`O(logn)`。
#### 例子：
举例如下：`addNum(1)`, 两个堆为`{}`， `{1}`; `addNum(2)`, 两个堆为`{1}`, `{2}`; `findMedian() = 1.5`, `addNum(3)`, 两个堆为`{1}`, `{2, 3}`; `findMedian() = 2`.