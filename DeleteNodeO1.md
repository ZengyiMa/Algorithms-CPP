
# 在O(1)时间删除链表结点

描述：给定单链表的头指针和一个结点指针，定义一个函数，在 O(1) 时间删除该节点。

思路：并不是一定需要得到被删除的结点的前一个结点，可以将被删除结点的后一个结点的内容复制到被删除结点，然后将后一个结点删除。

```
void deleteNode(Node *root, Node *toDeleteNode)
{
    if (root == NULL || toDeleteNode == NULL) return;
    if (root == toDeleteNode) {
        // 头结点
        root = NULL;
        return;
    } else if (toDeleteNode->next == NULL) {
        // 尾节点
        while (root->next != toDeleteNode) {
            root = root->next;
        }
        root->next = NULL;
    } else {
        // 中间
        Node *tempNode = toDeleteNode->next;
        toDeleteNode->next = tempNode->next;
        toDeleteNode->data = tempNode->data;
    }
}
```

