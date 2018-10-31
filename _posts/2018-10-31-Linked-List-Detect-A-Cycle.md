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

- [Hackerrank Linked Lists: Detect A Cycle](https://www.hackerrank.com/challenges/ctci-linked-list-cycle/problem)

## Idea

>C++ solution. Use slow and fast pointer, during the traversal, 
>slow pointer takes one step and fast takes two steps. 
>If there is a cycle in the list, the fast pointer will equal to slow pointer. 
>Otherwise, fast pointer will reach the tail first.

### C++ Solution

    bool has_cycle(Node* head) {

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

 

