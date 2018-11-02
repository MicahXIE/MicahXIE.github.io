---
layout:     post
title:      Palindrome Linked List
subtitle:   Slow and Fast Pointer 
date:       2018-11-02
author:     Micah
header-img: img/post-bg-cook.jpg
catalog: true
tags:
    - Algorithm
---

## Topic

- [Leetcode: Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/)

## Idea

>C++ solution. Use slow and fast pointer, during the traversal: 
>slow pointer takes one step and fast takes two steps
>slow pointer reverse its next to point to its prev
>when fast pointer reache the end of the linked list, slow will reach the middle
>Traverse the first and second half, compare each node value. if all equal, return true, otherwise return false

### C++ Solution

    class Solution {
    public:
        bool isPalindrome(ListNode* head) {
            if(head == NULL || head->next == NULL)
                return true;
        
            ListNode* prev = NULL;
            ListNode* slow = head;
            ListNode* fast = head;
        
            while(fast != NULL && fast->next != NULL){
                fast = fast->next->next;
                ListNode* next = slow->next;
                slow->next = prev;
                prev = slow;
                slow = next;
            }
        
            if(fast != NULL){
                slow = slow->next;
            }
        
            while(slow != NULL && prev != NULL){
                if(slow->val != prev->val)
                    return false;
                slow = slow->next;
                prev = prev->next;
            }
        
            return true;
        
        }
    };

 

