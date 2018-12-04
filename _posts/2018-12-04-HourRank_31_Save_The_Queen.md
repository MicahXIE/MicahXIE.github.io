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

- [HourRank 31: Save The Queen](https://www.hackerrank.com/contests/hourrank-31/challenges/save-the-queen)

***Details***

The kingdom of Zokoria is under attack! The invaders wish to capture the Queen and conquer Zokoria. Aware of the danger, Heldorf , the captain of the Zokorian army must devise an exit strategy for the Queen.

In order to do so, the invaders must be kept at bay for a period of time. There are n invaders who must be engaged in fight for as long as possible. The army has k soldiers, with each having the capability to fight for a total of a(i) seconds. The soldiers can fight against any invader at any time i.e. they can move to fight with another invader by dropping the current fight.

Heldorf wants you to find out how long does he have to help the Queen escape. You have to find the maximum possible time for which all the n invaders can be kept busy?

***Input Format***

The first line of input contains two numbers n and k - the number of invaders and the number of soldiers respectively.

The next line contains k numbers, each integer representing the time for which the respective soldier can engage in a fight.


***Constraints***

- 1 <= n <= k <= 10^4
- The time for which each solider can fight, a(i) , lies between 1 and 10^6.

***Output Format***

Print the maximum possible time for which the  invaders can be engaged in a fight. The number should be accurate up to 10^(-4) absolute precision.

***Example***

> Sample Input 0  
> 3 4    
> 1000 100 100 100      

> Sample Output 0    
> 150.000000000     
 
## Idea

> We can solve this problem by using Binary Search. We can define a function check(t) which tells if it 
> is possible to keep the invaders engaged for time t. Since this function is monotonically increasing in 
> nature, we can apply Binary Search here. For checking, we can assign a solider to an invader if t <= ai 
> else we can compute the total time we can allot to each invader. Now, since the time can be a real 
> number, we have to be careful about the precision while implementing Binary Search. One way we can do 
> get the correct answer is to iterate the Binary Search a fixed number of times so that all bits in the 
> answer have been found and no epsilon error is there.

### C++ Solution

    #include<bits/stdc++.h>
    using namespace std;


    int n,k,a[10007];

    int main(){
        cin>>n>>k;
        for(int i=0;i<k;i++){
            cin>>a[i];
        }   
        double lo = 0.0, hi = 1e15, mid; 
        for(int i = 0; i < 400; i++){ 
            mid = (lo+hi)/2; 
            int inv = n; 
            double req = 0.0; 
            for (int j = 0; j < k; j++) 
                if(a[j] >= mid){ 
                inv--; 
                }else{ 
                    req += a[j]; 
                } 
            if(inv <= 0){
                lo = mid; 
                continue;
            } 
            req /= inv; 
            if (req < mid) hi = mid; else lo = mid; 
        } 

        cout<<fixed<<setprecision(9)<<mid<<endl;
    }


 

