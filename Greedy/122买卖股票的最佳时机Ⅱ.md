# [122 买卖股票的最佳时机](https://leetcode.cn/problems/best-time-to-buy-and-sell-stock-ii/)

### 解题思路

只要次日价格比当天价格高,就可以各买入卖出一次,这样获取的利润是最大的.

可以通过反证法证明,假设存在其他利润更高的方案,则可能的情况:

1. 某日与次日的差值为负值, 必定使总和减小
2. 某日与次日的差值为零,并不会比当前的利润更大
3. 某日与次日的差值为正,但没有加上,必定使总和减小

### 代码实现

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        # Greedy
        result = 0
        for i in range(1, len(prices)):
            diff = prices[i] - prices[i - 1]
            if diff > 0:
                result += diff

        return result

```

