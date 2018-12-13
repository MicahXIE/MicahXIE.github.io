---
layout:     post
title:      The Hypertext Transfer Protocol (HTTP)
subtitle:   HTTP protocol
date:       2018-12-13
author:     Micah
header-img: img/post-bg-universe.jpg
catalog: true
tags:
    - Web Technology
---

## Background

The HTTP protocol enables web servers and browsers to exchange data over the 
Internet or an intranet. The World Wide Web Consortium (W3C), and international
community that develops standards, is responsible for revising and maintaining
this protocol.

In general an HTTP-based Uniform Resource Locator(URL) has below format:

>protocol://[host.]domain[:port][/context][/resource][?query string|path variable]

or

>protocol://IP address[:port][/context][/resource][?query string|path variable]
   
 
## HTTP Request

> `x^2 = a` can change to `x^2-a = 0` question. The question to get the square root of the number `a` can 
> convert to the question that to find a number `x` to make `x^2-a=0` (or very small number like 0.000001).
> Below method is to use Binary Search and keep narrowing the scope to find the `mid value` to fulfill equation.
> The `mid value` is the square root of number `a`.

### HTTP Response

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



 

