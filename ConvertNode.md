# 二叉搜索树与双向链表

描述:输入一棵二叉搜索树，将该二叉搜索树转换成一个排序的双向链表。要求不能创建任何新的结点，只能调整树中结点指针的指向。 

思路:
中序遍历树节点，使用了一个变量记录访问最后的节点值。

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
    TreeNode* Convert(TreeNode* root)
    {
        if (root == NULL) return NULL;
        TreeNode *lastNode = NULL;
        convertNode(root, &lastNode);
        while (lastNode != NULL && lastNode->left != NULL) {
            lastNode = lastNode->left;
        }
        return lastNode;
    }
    
    
    void convertNode(TreeNode *node, TreeNode **pLast) {
        if (node == NULL) return;
        if (node->left) {
            convertNode(node->left, pLast);
        }
        node->left = *pLast;
        if ((*pLast) != NULL) (*pLast)->right = node;
        (*pLast) = node;
        if (node->right) {
            convertNode(node->right, pLast);
        }
    }
};
```