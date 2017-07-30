
# 反转链表

描述：输入一个链表，反转链表后，输出链表的所有元素。

思路：递归遍历链表，递归的反转 2 个节点。


```
/*
struct ListNode {
	int val;
	struct ListNode *next;
	ListNode(int x) :
			val(x), next(NULL) {
	}
};*/
class Solution {
public:
    ListNode* ReverseList(ListNode* pHead) {
        if (pHead == NULL) return NULL;
        return ReverseResuriveList(pHead);
    }
    
    ListNode* ReverseResuriveList(ListNode* node) {
        if (node->next == NULL || node == NULL) {
            return node;
        }
       ListNode *head = ReverseResuriveList(node->next);
       node->next->next = node;
       node->next = NULL;
       return head;
    }
};
```