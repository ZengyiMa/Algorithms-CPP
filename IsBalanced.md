# 平衡二叉树

描述:输入一棵二叉树，判断该二叉树是否是平衡二叉树。


思路: 判断左右子树深度差距是不是为大于1，如果是大于1则不是

```
class Solution {
public:
    bool IsBalanced(TreeNode* pRoot) {
        if (pRoot == NULL) return true;
		int left = treeDepth(pRoot->left);
        int right = treeDepth(pRoot->right);
        int diff = abs(left - right);
        if (diff < 2) {
            return true;
        } else {
            return false;
        }
    }
    
    int treeDepth(TreeNode *root) {
        if (root == NULL) return 0;
        return max(treeDepth(root->left), treeDepth(root->right)) + 1;
    }
};
```