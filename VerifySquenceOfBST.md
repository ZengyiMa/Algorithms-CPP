# 二叉搜索树的后序遍历序列

描述：从上往下打印出二叉树的每个节点，同层节点从左至右打印。。

思路： 

     * 对于后序遍历来说，序列数组的最后一个元素一定是根节点,
     * 则根据这个元素，将前面的数组分为左、右两个部分，左侧部分都小，右侧部分都大，
     * 如果右侧部分有比该根节点小的元素，那么就不是后序遍历,如此递归进行。
     * 注意，这个树是二叉搜索树，做题注意下取完 root 要不 end 扣除。


```
class Solution {
public:
    bool VerifySquenceOfBST(vector<int> sequence) {
        if (sequence.size() == 0) return false;
		return verifySquenceOfBST(&sequence, 0, sequence.size() - 1);
    }
    
    bool verifySquenceOfBST(vector<int> *sequence, int start, int end) {
        if (start >= end) return true;
        int root = (*sequence)[end];
        int leftEnd = start;
        // 小于不等于 end 是因为最后一个是 root 已经被占用。
        // 找到左子树的分隔点。左子树都小于 root
        for (; leftEnd < end; leftEnd++) {
            if (root < (*sequence)[leftEnd]) {
                break;
            }
        }
		// 如果右子树发现有小于 root 那么这个树就不成立。
        for (int i = leftEnd; i < end; i++) {
            if (root > (*sequence)[i]) {
                return false;
            }
        }
        // 左子树递归和右子树递归。减去 root 
        return verifySquenceOfBST(sequence, start, leftEnd - 1) && verifySquenceOfBST(sequence, leftEnd, end - 1);
    }
    
    
};
```