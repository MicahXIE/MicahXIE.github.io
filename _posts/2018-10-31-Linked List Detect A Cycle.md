---
layout:     post
title:      Linked List Detect A Cycle
subtitle:   Slow and Fast Pointer
date:       2018-10-31
author:     Micah
header-img: img/post-bg-cook.jpg
catalog: true
tags:
    - Algorithm
---

## Topic

Hackerrank Linked Lists: Detect

- [Hackerrank Linked Lists: Detect A Cycle](https://www.hackerrank.com/challenges/ctci-linked-list-cycle/problem)

## Idea

>快慢指针的方法，就是让两个指针同时指向链表。在向后遍历的时候，一个指针每次走两步，称为快指针；
>一个指针每次走一步，称为慢指针。如果快慢指针相遇，则说明链表有环，否则无环。

### C++ Solution

bool has_cycle(Node* head) {
    // Complete this function
    // Do not write the main method
    if(head == NULL || head->next == NULL){
        return false;
    }
    
    Node* slow = head;
    Node* fast = head->next;
    
    while(slow != fast){
        if(fast == NULL || fast->next == NULL) return false;
        
        slow = slow->next;
        fast = fast->next->next;
        
    }
    
    return true;
}

 

