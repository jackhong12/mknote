# 2. Add Two Numbers

- [Leetcode: 2. Add Two Numbers](https://leetcode.com/problems/add-two-numbers/)

## Problem Statement
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

## Solutions
```cpp linenums="1"
ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
    int lead = 0;
    ListNode root;
    ListNode *ptr = &root;
    for (; l1 && l2; l1 = l1->next, l2 = l2->next) {
        int value = l1->val + l2->val + lead;
        ListNode *node = new ListNode(value % 10);
        lead = value / 10;
        ptr->next = node;
        ptr = ptr->next;
    }

    for (; l1; l1 = l1->next) {
        int value = l1->val + lead;
        ListNode *node = new ListNode(value % 10);
        lead = value / 10;
        ptr->next = node;
        ptr = ptr->next;
    }

    for (; l2; l2 = l2->next) {
        int value = l2->val + lead;
        ListNode *node = new ListNode(value % 10);
        lead = value / 10;
        ptr->next = node;
        ptr = ptr->next;
    }

    if (lead)
        ptr->next = new ListNode(lead);

    return root.next;
}
```

??? Note "Tags"
    - [[leetcode_medium|Leetcode Medium]]
    - [[linked_list|Linked List]]
