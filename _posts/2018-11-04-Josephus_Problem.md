---
layout:     post
title:      Josephus Problem
subtitle:   Linked List and Recursion 
date:       2018-11-04
author:     Micah
header-img: img/post-bg-cook.jpg
catalog: true
tags:
    - Algorithm
    - C++
    - Linked List
---

## Topic

In computer science and mathematics, the Josephus Problem (or Josephus permutation) 
is a theoretical problem. Following is the problem statement:
There are n people standing in a circle waiting to be executed. The counting out begins 
at some point in the circle and proceeds around the circle in a fixed direction. In each 
step, a certain number of people are skipped and the next person is executed. The elimination 
proceeds around the circle (which is becoming smaller and smaller as the executed people 
are removed), until only the last person remains, who is given freedom. 
Given the total number of persons n and a number k which indicates that k-1 persons are 
skipped and kth person is killed in circle. The task is to choose the place in the initial 
circle so that you are the last one remaining and so survive.

## Idea

>solution 1
>seq 1 ~ 1, 2, 3, 4, ... , n-2, n-1, n
>seq 2 ~ 1, 2, 3, 4, ... , k-1, k+1, ..., n-2, n-1, n
>seq 3 ~ k+1, k+2, k+3, ..., n-2, n-1, n, 1, 2, 3, .., k-2, k-1
>seq 4 ~ 1, 2, 3, 4, ... , 7, 8, ..., n-2, n-1

> ∵ k = m%n; 　　

> ∴ x' = x+k = x+ m%n ; 而 x+ m%n 可能大于n

> ∴x'= (x+ m%n)%n = (x+m)%n 　　

> 得到 x' is the value start from 0. final result need to add 1

>solution 2
>STL list common method

### C++ Solution

    #include <stdio.h> 
    #include <iostream>
    #include <list>
    using namespace std;

    //time complexsity: O(n)
    int josephus_solution1(int n, int m) 
    { 
        if (n == 1) 
            return 0; 
        else
            /* The position returned by josephus(n - 1, k) is adjusted because the 
            recursive call josephus(n - 1, k) considers the original position  
            k%n + 1 as position 1 */
            return (josephus_solution1(n - 1, m) + m) % n; 
    }


    //time complexsity: O(n*m)
    int josephus_solution2(int n, int m)
    {
        if(n < 1 || m < 1)
            return -1;

        list<int> jlist;

        for(int i=0; i<n; i++){
            jlist.push_back(i);

        }

        auto jiter = jlist.begin();

        while(jlist.size() > 1){
            for(int j=0; j<m-1; j++){
                jiter++;
                if(jiter == jlist.end()){
                    jiter = jlist.begin();
                }
            }

            auto jiter_del = jiter;

            if(++jiter == jlist.end()){
                jiter = jlist.begin();
            }

            jlist.erase(jiter_del);
        }

        return *jiter;

    }


// Driver Program to test above function 
int main() 
{ 
  int n = 14; 
  int m = 2; 
  printf("The chosen place is %d\n", josephus_solution1(n, m)+1);
  printf("The chosen place is %d\n", josephus_solution2(n, m)+1); 

  return 0; 
} 

