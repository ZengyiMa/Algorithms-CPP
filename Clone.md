# 复杂链表的复制

描述:输入一个复杂链表（每个节点中有节点值，以及两个指针，一个指向下一个节点，另一个特殊指针指向任意一个节点），返回结果为复制后复杂链表的head。
思路:

1. 复制每个节点，如：复制节点A得到A1，将A1插入节点A后面
2. 遍历链表，A1->random = A->random->next;
3. 将链表拆分成原链表和复制后的链表



```
/*
struct RandomListNode {
    int label;
    struct RandomListNode *next, *random;
    RandomListNode(int x) :
            label(x), next(NULL), random(NULL) {
    }
};
*/
class Solution {
public:
    RandomListNode* Clone(RandomListNode* pHead)
    {
        if (pHead == NULL) return NULL;
        
        // 第一步，先把要复制的加入到链表原来每个元素的后面
        RandomListNode *p = pHead;
        while (p != NULL) {
            RandomListNode *node = new RandomListNode(p->label);
            node->next = p->next;
            p->next = node;
            p = node->next; 
        }
        
        // 第二步 处理下 random 节点
        p = pHead;
        while (p != NULL) {
            if (p->random != NULL) {
                 p->next->random = p->random->next;
            }
            p = p->next->next;
        }
        
        // 第三步 去除原来的节点
        RandomListNode *cloneHead = pHead->next;
        p = pHead;
        while (p->next != NULL) {
            RandomListNode *tmp = p->next;
            p->next = tmp->next;
            p = tmp;
        }
        return cloneHead;
    }
};
```