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

## Common Abbreviations

- Global
	
	**SGA**: System Global Area      
	**PGA**: Program Global Area      

- Database Language
	
	**DML**: data manipulation language (insert, delete, update, select)       
	**DDL**: data definition language (create, alter, drop, truncate) -- TABLE level     
	**DCL**: data control language (grant, deny, revoke) -- Permission    

- Database Process

	**DBWn**: Database Block Writer    
	**CKPT**: Checkpoint Process     
    **LGWR**: Log Writer    

- Communication Protocol     

	**BGP**: Border Gateway Protocol     

## Structure


![Oracle Architecture](https://www.siue.edu/~dbock/cmis565/module1-architecture_files/image004.jpg)


- Connection
Connection: Bidirectional network pathway between a user process on a client or mid tier 
and an Oracle process on the server.    

Session: Representation of a specific login by a user.     

- Program Global Area    
PGA (Program Global Area) is a memory area that contains:    
    Session information    
    Cursor information    
    SQL execution work areas:        
        Sort area    
        Hash join area    
        Bitmap merge area    
        Bitmap create area  

Work area size influences SQL performance    

Work areas can be automatically or manually managed     


















