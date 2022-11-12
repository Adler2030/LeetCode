# 解题模板

最后我们需要来计算一下卡特兰数的通项 Cn=C2nnn+1

卡特兰数满足以下递推式：

（证明从略）$$C_1 =1,C_n=C_{n-1}(4*n-2)/(n+1)$$

因此，我们可以通过递推来得到第 n 个卡特兰数。

```python
// Some code
ans, n = 1, 20
print("1:" + str(ans))
for i in range(2, n + 1):
    ans = ans * (4 * i - 2) // (i + 1)
    print(str(i) + ":" + str(ans))
```

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>
