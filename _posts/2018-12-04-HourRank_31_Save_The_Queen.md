---
layout:     post
title:      HourRank 31 Save the Queen -- Binary Search
subtitle:   Binary Search
date:       2018-12-04
author:     Micah
header-img: img/post-bg-cook.jpg
catalog: true
tags:
    - Algorithm
---

## Topic

- [Hackerrank Linked Lists: Inserting A Node Into Doubly Linked List](https://www.hackerrank.com/challenges/insert-a-node-into-a-sorted-doubly-linked-list/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=linked-lists)

## Idea

>C++ solution. Doubly Linked List Basic Usage. Need to consider both previous and next nodes when
>insert a node. Also, need to consider the head and tail scenarios. 

### C++ Solution

    /*
    * For your reference:
    *
    * DoublyLinkedListNode {
    *     int data;
    *     DoublyLinkedListNode* next;
    *     DoublyLinkedListNode* prev;
    * };
    *
    */
    DoublyLinkedListNode* sortedInsert(DoublyLinkedListNode* head, int data) {
    
        DoublyLinkedListNode* node = new DoublyLinkedListNode(data);
    
        if(!head) {
            return node;    
        }
    
        if(data < head->data){
            node->next = head;
            head->prev = node;
            return node;
        } else {
        
            DoublyLinkedListNode* prev_node = NULL;
            DoublyLinkedListNode* cur_node = head;
        
            while(cur_node != NULL){
            
                if(cur_node->data >= data){
                    node->next = cur_node;
                    node->prev = prev_node;
                    //need to consider both previous and next nodes!
                    prev_node->next = node;
                    cur_node->prev = node;
                
                    return head;
                }
            
                prev_node = cur_node;
                cur_node = cur_node->next;
            }
        
            node->prev = prev_node;
            prev_node->next = node;
        
            return head;
        }
    
        return head;

    }

 

