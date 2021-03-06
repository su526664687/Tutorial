## 题目分析

给定一个串，求出所有的切分方式使得切出来的每一块都是单词表里的词。

### 解题思路

这题和Leetcode 132很像，同样是切分，同样是切分出来的要满足一定条件，不同的是
这题要输出所有的可能性。

同样考虑dp，我们令dp[i]代表一个集合，存dp状态转移的时候的所有可能转移，即dp[i]={j|子串(j,i)是一个单词，并且dp[j-1]不为空}。建立好这样的转移后，我们就可以从后往前搜。

举个例子：
s = `catsanddog`, dict = [`cat`, `cats`, `and`, `sand`, `dog`]，为了方便，我们从1开始数字母，把0留给一个空字符。那么：
```
dp[0]={0}
dp[1]={}
dp[2]={},
dp[3]={1},因为子串(1,3)是一个单词cat
dp[4]={1},因为子串(1,4)是一个单词cats
dp[5]={},
dp[6]={},
dp[7]={4,5},因为子串(4,7)=`sand`,(5,7)=`and`，并且dp[3],dp[4]不为空
dp[8]={},
dp[9]={},
dp[10]={8},因为(8,10)=`dog`并且dp[7]不为空。
```
处理出之后，我们从10开始搜索，dp[10]只有8，因此下一步我们只能从7搜，7有4,5两个可以转移，假设我们选了4，那么我们看dp[3],它只包含1，因此我们只能选1，然后发现我们就走到了0节点，就搜出了一条路径。
