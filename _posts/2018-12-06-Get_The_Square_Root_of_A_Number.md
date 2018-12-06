---
layout:     post
title:      Square Root of A Number -- Binary Search
subtitle:   Binary Search
date:       2018-12-06
author:     Micah
header-img: img/post-bg-cook.jpg
catalog: true
tags:
    - Algorithm
---

## Topic

- [LeetCode 69: Sqrt(x)](https://leetcode.com/problems/sqrtx/)
   
 
## Idea

> x^2 = a can change to x^2-a = 0 question. The question to get the square root of the number a can 
> convert to the question that to find a number x to make x^2-a=0 (or very small number like 0.000001)
> Below method is to use Binary Search and keep narrowing the scope to find the mid value to fulfill equation
> The mid value is the square root of number a

### C++ Solution

    #include<iostream>
    #include<math.h>
    using namespace std;

    double calculate_Square_Root(int n)
    {
        double mid =(double (n))/ 2;
        double l = 0.0, r = 1.0;
        while (fabs((mid*mid - (double)n)) > 0.000001)
        {

            if ((mid*mid - (double)n) > 0.000001)
            {
                r = mid;
                mid = l + (r - l) /2;
            }

            else
            {

                l = mid;
                mid = l + (r - l) / 2;
            }

        }
        return mid;

    }

    int main(){
    
        double res = calculate_Square_Root(7);
        cout << "result: " << res << endl;
    }



 

