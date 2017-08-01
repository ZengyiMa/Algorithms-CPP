
# 二叉树的镜像

描述：操作给定的二叉树，将其变换为源二叉树的镜像。

思路：递归遍历树，交互左右 2 个节点。

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
    void Mirror(TreeNode *pRoot) {
		if (pRoot == NULL) return;
        TreeNode *tmp = pRoot->left;
        pRoot->left = pRoot->right;
        pRoot->right = tmp;
        Mirror(pRoot->left);
        Mirror(pRoot->right);
    }
};
```