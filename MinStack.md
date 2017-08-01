
# 包含 min 函数的栈

描述：定义栈的数据结构，请在该类型中实现一个能够得到栈最小元素的min函数。

思路：利用 2 个栈，第一个是数据栈，第二个是辅助栈，辅助栈只在当有比 top 小的时候才入栈新元素，否则入栈栈顶元素，这样，辅助栈总是会在 o(1) 的时间得到 min

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