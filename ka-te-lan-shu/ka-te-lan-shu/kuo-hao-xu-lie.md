# 括号序列

**题目描述**

&#x20;       n 对括号，则有多少种 “括号匹配” 的括号序列

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

**思路**

&#x20;       左括号看成 +1，右括号看成 -1，那么就和上题的进出栈一样，共有 $$C^{n+1}_{2n}$$ 种序列。
