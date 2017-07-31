
# 树的子结构

描述：输入两棵二叉树A，B，判断B是不是A的子结构。

思路：递归遍历树，查找左右节点判断是否子树。

```
/*
struct TreeNode {
	int val;
	struct TreeNode *left;
	struct TreeNode *right;
	TreeNode(int x) :
			val(x), left(NULL), right(NULL) {
	}
};*/
class Solution {
public:
    bool HasSubtree(TreeNode* pRoot1, TreeNode* pRoot2)
    {
		if (pRoot1 == NULL || pRoot2 == NULL) return false;
        return hasSameNode(pRoot1, pRoot2) || HasSubtree(pRoot1->left, pRoot2) || HasSubtree(pRoot1->right, pRoot2);
    }
    
    
    bool hasSameNode(TreeNode* pRoot1, TreeNode* pRoot2) {
       	if (pRoot2 == NULL) return true;
        if (pRoot1 == NULL) return false;
		if (pRoot1->val == pRoot2->val) {
        	return hasSameNode(pRoot1->left, pRoot2->left) && hasSameNode(pRoot1->right, pRoot2->right);
        } else {
            return false;
        }
    }
};
```