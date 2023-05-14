---
title: "低级指针操作"
date: 2020-01-09T21:06:35+08:00
draft: false
---

#### 如何使用二级指针对单链表进行删除操作

假设要删除的单链表有一个head结点指向实际结点

```c
typedef struct _node {
        long long data;
        struct _node *next;
} Node;

// 比较函数
typedef bool (* condition)(const Node *node);
bool cmp(const Node *node)
{
        if (node->data % 2) // 删除数值为奇数的节点
                return true;
        return false;
}

// 删除函数
void ll_remove(Node **curr, condition need_delete)
{ // curr指向head，head指向首节点
        Node *entry;
        while (*curr)
        {
                entry = *curr; // entry指向当前要处理的节点
                if (need_delete(entry))
                { // 删除当前节点，就把curr指向的指针指向下一个节点
                        *curr = entry->next;
                        free(entry);
                } // 不删除当前节点，就把curr指向当前节点的next域
                else
                        curr = &(entry->next);
        }
}

int main(int argc, char *argv[])
{
        // 构建链表
        Node *head = NULL, *temp = NULL;
        for (int i = 10; i != 0; --i)
        {
                temp = (Node *)malloc(sizeof(Node));
                temp->data = i;
                temp->next = head;
                head = temp;
        }
        // 删除奇数节点
        ll_remove(&head, cmp);
}
```

解释：如果按照标准写法，将head作为参数传入remove函数，不仅需要一个prev和一个curr来保存前一个指针和当前指针，还要考虑删除第一个节点的特殊情况。

上面的写法则用一个二级指针指向head巧妙地将所有节点都统一处理，无论是不是第一个节点，都是curr指向的指针所指向的节点。

需要删除当前节点时让curr所指的指针指向下一个节点，不需要删除当前节点时，就让curr指向当前节点的next域。

