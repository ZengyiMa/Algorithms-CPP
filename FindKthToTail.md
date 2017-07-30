
# 链表中倒数第k个结点

描述：输入一个链表，输出该链表中倒数第k个结点。

思路：使用双指针，一个位于头部 s 指针，一个位于头部之后的第 K 个的位置的 e 指针，然后 e 走到末尾，s 的位置与其同步往后移，那么 s 所在的位置就是倒数第 K 个

思路：
n值可能较大，所以此题为大数问题。大数问题一般可通过字符串或者数组来模拟解决。使用整数数组通过递归实现，即打印i位表示的整数，假设i-1表示的整数可列举，则只需将第i位从0到9遍历，同时与i-1位
表示的整数序列组合即可。复杂度为O(10^n)。


```
struct ListNode {
	int val;
	struct ListNode *next;
	ListNode(int x) :
			val(x), next(NULL) {
	}
};*/
class Solution {
public:
    ListNode* FindKthToTail(ListNode* pListHead, unsigned int k) {
        if (pListHead == NULL || k == 0) return NULL;
    	ListNode *s = pListHead;
        ListNode *e = pListHead;
        for (int i = 1; i < k; ++i) {
            if (e->next != NULL) {
                e = e->next;
            } else {
                return NULL;
            }
        }
        
        // e 走到 尾部。那么s 也会找到最后的第K个
        while (e->next != NULL) {
            e = e->next;
            s = s->next;
        }
        
        return s;
    }
};
```