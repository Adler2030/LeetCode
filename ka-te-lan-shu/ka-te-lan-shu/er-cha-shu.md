# 二叉树

**题目描述**

`n + 1` 个叶子节点能够构成多少种形状不同的（国际）满二叉树

（国际）满二叉树定义：如果一棵二叉树的结点要么是叶子结点，要么它有两个子结点，这样的树就是满二叉树。

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

**思路**

使用深度优先搜索这个满二叉树，向左扩展时标记为 +1，向右扩展时标记为 -1。

由于每个非叶子节点都有两个左右子节点，所有它必然会先向左扩展，再向右扩展。总体下来，左右扩展将会形成匹配，即变成进出栈的题型。`n + 1`个叶子结点会有 2n 次扩展，构成 $$C^{n+1}_{2n}$$种形状不同的满二叉树。

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>
