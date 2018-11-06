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

## Common Abbreviation

SGA: System Global Area
PGA: Program Global Area

DML: data manipulation language (insert, delete, update, select)
DDL: data definition language (create, alter, drop, truncate) -- TABLE level
DCL: data control language (grant, deny, revoke) -- Permission

DBWn: Database Block Writer
CKPT: Checkpoint Process
LGWR: Log Writer

BGP: Border Gateway Protocol

其实这三个进程都是为了更好地完成一件事：安全高效地实现内存数据块写入数据文件，就是将内存中修改的数据反映到硬盘的数据文件上。 

## Structure

![](https://github.com/MicahXIE/MicahXIE.github.io/blob/master/img/oracle_architecture.jpeg)






