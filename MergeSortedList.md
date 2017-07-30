# 合并两个排序的链表

描述：输入两个单调递增的链表，输出两个链表合成后的链表，当然我们需要合成后的链表满足单调不减规则。

思路：双指针，比较大小，一次插入相应的位置


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
    ListNode* Merge(ListNode* pHead1, ListNode* pHead2)
    {
        if (pHead1 == NULL) return pHead2;
        if (pHead2 == NULL) return pHead1;
        ListNode *head = pHead1;
        ListNode *p1 = pHead1->next;
        ListNode *p2 = pHead2;
        if (pHead1->val > pHead2->val) {
            head = pHead2;
            p1 = pHead1;
            p2 = pHead2->next;
        } 
        ListNode *root = head;
        while (p1 != NULL && p2 != NULL) {
            if (p1->val > p2->val) {
                head->next = p2;
                p2 = p2->next;
            } else {
                head->next = p1;
                p1 = p1->next;
            }
            head = head->next;
        }
        
        p1 = p1 == NULL ? p2 : p1;
         while (p1 != NULL) {
                head->next = p1;
                head = p1;
                p1 = p1->next;
            }
        return root;
        
    }
};
```