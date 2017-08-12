# 两个链表的第一个公共结点

描述:输入两个链表，找出它们的第一个公共结点。

思路: 找出2个链表的长度，然后让长的先走两个链表的长度差，然后再一起走
（因为2个链表用公共的尾部）

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
    ListNode* FindFirstCommonNode(ListNode* pHead1, ListNode* pHead2) {
        if (pHead1 == NULL || pHead2 == NULL) return NULL;
        ListNode *h1 = pHead1;
        ListNode *h2 = pHead2;

        int h1Leght = 0;
        int h2Leght = 0;
        while (h1 != NULL || h2 != NULL) {
            if (h1 != NULL) {
                h1 = h1->next; 
                h1Leght++;
            }
            if (h2 != NULL) {
                h2 = h2->next;
                h2Leght++;
            }
        }
        h1 = pHead1;
        h2 = pHead2;
        if (h1Leght < h2Leght) {
            for (int i = 0; i < h2Leght - h1Leght; ++i) {
               h2 = h2->next; 
            }
        } else if (h1Leght > h2Leght){
            for (int i = 0; i < h1Leght - h2Leght; ++i) {
               h1 = h1->next; 
            }
        }

        while (h1 != NULL && h2 != NULL) {
            if (h1 == h2) {
                return h1;
            }
            h1 = h1->next;
            h2 = h2->next;
        }
        return NULL;
    }
};
```