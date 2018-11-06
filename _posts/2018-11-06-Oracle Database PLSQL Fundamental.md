---
layout:     post
title:      Oracle Database PLSQL Fundamentals
subtitle:   Basic Stucture and Flow 
date:       2018-11-06
author:     Micah
header-img: img/post-bg-cook.jpg
catalog: true
tags:
    - Oracle

---

## Topic

SGA: System Global Area
PGA: Process Global Area

DML: data manipulation language (insert, delete, update, select)
DDL: data definition language (create, alter, drop, truncate) -- TABLE level
DCL: data control language (grant, deny, revoke) -- Permission

DBWn: Database Block Writer
CKPT: Checkpoint Process
LGWR: Log Writer

其实这三个进程都是为了更好地完成一件事：安全高效地实现内存数据块写入数据文件，就是将内存中修改的数据反映到硬盘的数据文件上。 

https://www.cnblogs.com/chengxiao/p/5904783.html

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

## Structure



### Flow


