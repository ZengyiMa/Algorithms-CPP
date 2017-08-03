# 二叉树中和为某一值的路径

描述:输入一颗二叉树和一个整数，打印出二叉树中结点值的和为输入整数的所有路径。路径定义为从树的根结点开始往下一直到叶结点所经过的结点形成一条路径。

思路:由于要先访问节点，我们可以使用前序遍历二叉树，遍历到一个节点，使用一个数组来保存路径，
    如果是叶节点，判断路径中的和是不是和期望的数字相同，回溯的时候将路径 pop 即可



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
    vector<vector<int> > FindPath(TreeNode* root,int expectNumber) {
        vector<vector<int> > results;
        vector<int> path;
        findPath(root, &results, &path, expectNumber);
        return results;
    }

   void findPath(TreeNode* root, vector<vector<int> > *result, vector<int> *path,int expectNumber) {
        if (root == NULL) return;
        path->push_back(root->val);
        // 判断是不是叶节点
        if (root->left == NULL && root->right == NULL) {
            int total = 0;
            for(int i = 0; i < path->size(); ++i) {
                total += (*path)[i];
            }
            if (total == expectNumber) {
                vector<int> currentPath(*path);
                result->push_back(currentPath);
            }
        } 
        findPath(root->left, result, path, expectNumber);
        findPath(root->right, result, path, expectNumber);
        // 回溯
        path->pop_back();
    }
};
```