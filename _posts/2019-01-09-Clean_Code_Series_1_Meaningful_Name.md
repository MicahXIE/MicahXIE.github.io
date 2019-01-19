---
layout:     post
title:      Meaningful Name
subtitle:   Clean Code Series
date:       2019-01-09
author:     Micah
header-img: img/post-bg-universe.jpg
catalog: true
tags:
    - coding standards
---

## Background

Clean code is definitely a great book to improve the state of the art of software craftsmanship. 
In this series, I will summerize some key points in this book and for details please refer to the book 
`Clean Code Robert C. Martin Series`


## Rules & Examples

Names are everywhere in software. We name our variables, our functions, our arguments, classes, and packages. We name our source files and the directories that contain them. We name our jar files and war files and ear files. 



**Use Intention-Revealing Names**

It is easy to say that names should `reveal intent`. What we want to impress upon you is that we are serious about this. Choosing good names takes time but `saves more` than it takes. Choosing names that reveal intent can make it `much easier` to understand and change code. 

What is the purpose of this code?

```Java
public List<int[]> getThem() {
	List<int[]> list1 = new ArrayList<int[]>(); 
	for (int[] x : theList)
		if (x[0] == 4) 
			list1.add(x);
	return list1; 
}
```

Say that we’re working in a mine sweeper game. We find that the board is a list of `cells` called `theList`. Let’s rename that to `gameBoard`. we can improve the code considerably:

```Java
public List<int[]> getFlaggedCells() {
	List<int[]> flaggedCells = new ArrayList<int[]>(); 
	for (int[] cell : gameBoard)
		if (cell[STATUS_VALUE] == FLAGGED) 
			flaggedCells.add(cell);
	return flaggedCells; 
}
```

We can go further and write a simple `class for cells` instead of using `an array of ints`. It can include an intention-revealing function (call it isFlagged) to hide the magic numbers. It results in a new version of the function:

```Java
public List<Cell> getFlaggedCells() {
	List<Cell> flaggedCells = new ArrayList<Cell>(); 
	for (Cell cell : gameBoard)
		if (cell.isFlagged()) 
			flaggedCells.add(cell);
	return flaggedCells; 
}
```

 

**Avoid Disinformation**

Programmers must avoid leaving false clues that obscure the meaning of code. We should avoid words whose entrenched meanings vary from our intended meaning.

`hp, aix, and sco` would be poor variable names because they are the names of `Unix platforms or variants`. 

Do not refer to a grouping of accounts as an `accountList` unless it’s `actually a List`.

Beware of using names which vary in `small ways`. How long does it take to spot the subtle difference between a `XYZControllerForEfficientHandlingOfStrings` in one module and, somewhere a little more distant, `XYZControllerForEfficientStorageOfStrings`?


**Make Meaningful Distinctions**

```Java
getActiveAccount(); 
getActiveAccounts(); 
getActiveAccountInfo();
```

How are the programmers in this project supposed to know which of these functions to call?


In the absence of specific conventions, the variable moneyAmount is indistinguishable from money, customerInfo is indistinguishable from customer, accountData is indistinguishable from account, and the Message is indistinguishable from message. Distinguish names in such a way that the reader knows what the differences offer.















**