title: Top Data Structures and Algorithm Interview Questions
date: 2014-08-06 15:38:26
category: [interview]
tags: [data structure,algorithm,interview]
---

##String

**How to reverse String in Java ?**

**Write code to check a String is palindrome or not?**

**Write a method which will remove any given character from a String?**

**Print all permutation of String both iterative and Recursive way?**

**Write a function to find out longest palindrome in a given string?**

##Number

**Write code to check whether a number is power of two or not?**

**Write a program to check whether a number is palindrome or not?**

**Write code to check whether a number is Armstrong no or not** 

**Write a program to find all prime number up to a given numbers?**

**Write function to compute Nth Fibonacci number? Both iterative and recursive?**


##Array

**In an array 1-100 exactly one number is duplicate how do you find it?**

1. `hashset`
2. switch with index?

**In an array 1-100 many numbers are duplicates, how do you find it?**

1. `hashmap`

**Given two arrays, 1,2,3,4,5 and 2,3,1,0,5 find which number is not present in the second array.**

put the elements of the second array in the Hashtable and for every element of the first array, check whether it’s present in the hash or not

**How do you find second highest number in an integer array?**


## Stack & Queue

**What is difference between Stack and Queue**

Stack: FILO
Queue: FIFO

**Write a Java program to implement Stack**

**Write a Java program to implement Queue only with Stack**

**How would you implement a queue using two stacks?**


##LinkedList

**How to implement your own LinkedList**

**How do you find middle element of a linked list in single pass?**

Use two pointers with one increasing one step and the other increasing two step simultaneously, so by the time the first pointer reaches the end of linked list, the second pointer will point to the middle element.

**How do you find 3rd element from last in single pass?**

Apply the similar approach above. Use two pointers with one increasing one step and the other increasing two step at a time, and by the time the first pointer reaches the end of linked list, the second pointer will point to the 3rd element.


**How do you find if there is any loop in singly linked list? How do you find the start of the loop?**

**How do you reverse a singly linked list?**

**What is difference between Singly Linked List and Doubly Linked List**

In a single linked list, node only points towards next node, and there is no pointer to previous node, which means you can not traverse back on a singly linked list. On the other hand doubly linked list maintains two pointers, towards next and previous node, which allows you to navigate in both direction in any linked list.

**How to reverse linked list using recursion and iteration**

## Sorting & Searching

**Write a Java program to sort a array using Bubble Sort/Insertion algorithm?**

**Write a program to sort numbers using quick sort?**

**Write a program to implement binary search algorithm**

**How do you sort Java object using Comparator?**

## Tree

**What is binary search tree**

Binary Search Tree has some special properties e.g. left nodes contains items whose value is less than root , right sub tree contains keys with higher node value than root, and there should not be any duplicates in the tree.

**How do you find depth of binary tree?**

**Write code to print InOrder traversal of a tree?**

**Print out all leaf node of a binary tree?**

## Hash

**Write your own HashMap/Hashtable implementation**

## Recusive or DP


