
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
      ListNode* ReverseList(ListNode* node) {
        if (node == NULL || node->next == NULL) {
            return node;
        }
       ListNode *head = ReverseList(node->next);
       node->next->next = node;
       node->next = NULL;
       return head;
    }
};

// 非递归
class Solution {
public:
    ListNode* ReverseList(ListNode* pHead) {
		
        if (pHead == NULL) return NULL;
        ListNode *now = pHead;
        ListNode *pre = NULL;
		ListNode *p = NULL;
        while (now != NULL) {
            ListNode *tmp = now->next;
            now->next = pre;
            pre = now;
            now = tmp;
        }	
        return pre;
    }
};
```