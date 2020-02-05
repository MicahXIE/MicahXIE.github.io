---
layout:     post
title:      Java Garbage Collection Flow
subtitle:   
date:       2020-02-04
author:     Micah
header-img: img/post-bg-unix-linux.jpg
catalog: true
tags:
    - Java JVM
---

## Background
This article mainly summarize the Java JVM garbage collection flow based on HotSpot VM (most popular VM).


## Mainstream VM 
* HotSpot VM (Oracle)
* J9 VM (IBM)
* Zing VM (Azul)


## Introduction

### JRE & JDK
- When you download Java, you get the Java Runtime Environment (JRE). The JRE consists of the Java Virtual Machine (JVM), Java platform core classes, and supporting Java platform libraries. All three are required to run Java applications on your computer.

- The Java Development Kit (JDK) is a collection of tools for developing Java applications. With the JDK, you can compile programs written in the Java Programming language and run them in a JVM. In addition, the JDK provides tools for packaging and distributing your applications.


### Java Virtual Machine (JVM)
- The Java virtual machine knows nothing of the Java programming language, only of a particular binary format, the class file format. A class file contains Java virtual machine instructions (or bytecodes) and a symbol table, as well as other ancillary information. It is not inherently interpreted, but can just as well be implemented by compiling its instruction set to that of a silicon CPU. It may also be implemented in microcode or directly in silicon.


### Hotspot JVM Architecture
![HotSpot JVM Architecture](https://images.app.goo.gl/7pGdJv4yHUE4eCu49)





