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
![HotSpot JVM Architecture](https://img.javatt.com/bf/bf82cfc64dac4b7fddfab3d438e5054d.png)


- When Java program executes, the JVM process will run. When Java program stops, the JVM process will end.
- Each Java program will start `one` JVM process.
- Class Loader Subsystem will provide 3 types of class loaders.
  1. `BootStrap ClassLoader`: load JDK core libs like rt.jar, resources.jar、charsets.jar etc.
  2. `Extension ClassLoader`: load JAVA_HOME jre/lib/ jar libs or -Djava.ext.dirs libs
  3. `App ClassLoader`: load application CLASSPATH jar and class files.
- `Method Area` stores class info, class static variable and constant pool. In Java program, all the threads share one `Method Area` so it must be thread-safe.
- `JVM Heap` : When Java program create or new an object instance, it will allocate memory in the heap. JVM only have one `JVM Heap` and all the threads will share this heap. We can dynamically set the memory size for JVM heap when run the java program.
- `Java Threads` （Java Stack): only store basic Java data type and object reference (not instance). The data will be released automatically once they go out of the scope. Every thread has it own stack and the stack is private. Every stack includes serveral stack frames. Each frame includes local variables area, operand stack area and runtime environment area.
- `Native Internal threads`: is similar to Java stack. `Native Internal Stack` is used when JVM calls native method. These methods are not written by Java(like C, C++ etc) and not managed by JVM.





