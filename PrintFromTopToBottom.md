# 树的广度优先遍历

描述：从上往下打印出二叉树的每个节点，同层节点从左至右打印。。

思路： 使用一个队列，每次遍历都把左右节点放入队列（如果有），直到队列为空结束。

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
    vector<int> PrintFromTopToBottom(TreeNode* root) {
        vector<int> result;
        if (root == NULL) return result;
        deque<TreeNode *> queue;
        queue.push_back(root);
        while (!queue.empty()) {
            TreeNode* node = queue.front();
            queue.pop_front();
            result.push_back(node->val);
            if (node->left != NULL) queue.push_back(node->left);
            if (node->right != NULL) queue.push_back(node->right);
        }
        return result;
    }
};
```