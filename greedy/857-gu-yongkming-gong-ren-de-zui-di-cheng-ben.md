# [855 雇佣K名工人的最低成本](https://leetcode.cn/problems/minimum-cost-to-hire-k-workers/)

### 解题思路



> 由于“工资组中的每名工人至少应当得到他们的最低期望工资”，故对于任意一工人i，其工作质量，期望工资存在以下条件：
> $$
> total cost * quality[i]/totalquality >= wage[i]
> $$
> ，即
> $$
> total cost >= wage[i]/quality[i]*totalquality
> $$



所以当工作质量总和一定时，总花费的范围是由 wage[i]/quality[i] 最大值决定的，于是便可以用贪心算法

1. 在此基础上，我们可以zip两个列表，按 wage[i]/quality[i] 排序，取前k-1个元素，计算工作质量和值，并添加工作质量到一个先进先出队列中
2. 之后枚举k-1后的元素，假设此时的x为工资组中权重最高的，然后只需要在权重小于x的集合中选择工作质量最少的k-1个即可，每次遍历取ans与 wage[i]/quality[i]*total_quality最小值，并将小于当前权重的集合中工作质量最大的一个去除，添加新的工作质量，来获取最小花费



### 代码实现

```python
class Solution:
    def mincostToHireWorkers(self, quality, wage, k):
        cost_performance = sorted(zip(wage, quality), key=lambda x: x[0] / x[1])
        totalq = 0
        ans = inf
        heap = []
        
        for _, q in cost_performance[:k-1]:
            totalq += q
            heappush(heap, -q)
        for w, q in cost_performance[k-1:]:
            totalq += q
            heappush(heap, -q)
            ans = min(ans, w / q * totalq)
            totalq += heappop(heap)
        
        return ans
```



### Note

1. python 中堆默认是最小堆，而本题中需要弹出最大值，所以在压入的时候加了负号
2. 贪心算法：贪心算法（greedy algorithm，又称贪婪算法）是指，在对问题求解时，总是做出在当前看来是最好的选择。也就是说，不从整体最优上加以考虑，算法得到的是在某种意义上的局部最优解。
