## 题目

给定一个二叉树，找出其最大深度。

二叉树的深度为根节点到最远叶子节点的最长路径上的节点数。

说明: 叶子节点是指没有子节点的节点。

示例：
给定二叉树 [3,9,20,null,null,15,7]，

        3
       / \
      9  20
        /  \
       15   7

返回它的最大深度 3 。

## 思路

1. 递归

## 代码

```c
int maxDepth(struct TreeNode* root){
    int deep = 0;
    if (root != NULL) {
        int leftdeep = maxDepth(root->left);
        int rightdeep = maxDepth(root->right);
        deep = leftdeep >= rightdeep ? leftdeep + 1 : rightdeep + 1;
    }

    return deep;
}
```