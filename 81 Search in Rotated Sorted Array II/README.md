# 题目分析
题意要求我们在数组中找到特定的值，并返回。

### 解题思路（1）
最容易想到的就是线性扫描一遍数组，找到就返回，没找到就不返回，时间复杂度为0(n)
### 解题思路（2）
要想比0(n)更快、我们发现不能对数组进行排序，因为排序中最快的算法就是0（nlogn）级别的。题目我们可以找到转折的那个点比如4,5,6,7,0,1,2转折点是7,7左边都比4（最左边）小，7的右边都比4小。  

二分可以找到，找到这个点之后，后面的就好办了，我们拆成了俩个有序的数组，每一个再用二分方法来查找，最后的结果时间复杂度为0(log^{n} ).下面我说一下如何二分找到那个关键点位置，当num[mid]对应的值比最左边值大的时候，转折点肯定在右边，那么将left改为mid+1，当num[mid]对应的值比最左边值小的时候，转折点肯定在左边，这时将right = mid-1，当等于的时候,left++，那么出来while循环，找到的就是转折点的位置.

###解题思路（3）
本题采用二分法实现，但是比较挠头的是边界问题，而且元素有重复，相比纯粹递增的数组难度要大得多，要解决这个问题，首先要对所有可能情况进行分类，然后对每种可能的类别进行相应的处理。  

暂且不考虑nums[mid] = nums[left]的情况，本题大致可以简化为上图两种情况，可能的情况划分出来，那么解决本题就比较容易了：

当 nums[mid] = nums[left] 时，这时由于很难判断 target 会落在哪，那么只能采取 left++

当 nums[mid] > nums[left] 时，这时可以分为两种情况，判断左半部比较简单（如果target不在左边这部分，那么我们是可以直接去掉左边这部分的）

详细实现见solution.cpp

当 nums[mid] < nums[left] 时，这时可以分为两种情况，判断右半部比较简单(如果target不在右边这部分，那么我们也是可以直接去掉右边这部分的)