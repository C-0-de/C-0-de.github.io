---
layout: post
title:  "Tutorial Point Variables"
comments: true
tags:
    - general programming
    - beginner
    - variables
---
## Foreword
 There are a lot of programming tutorials available online which all want to get you started fast. This is important, but the very foundations of programming should be solid.

These foundations, which I will refer to as the Pillars of Programming, include:
- variables
- iterations and loops
- conditionals
- functions

 In this post, I will be focusing on variables.

## What's in a name?
Think of a variable as being akin to a label. It is a fancy way of assigning a name to a piece of information / value.

Once you have assigned a label to a value, the computer will be able to remember it for later use.
*Think of playing with label maker*
In most programming languages there are three parts to making a variable. These are the declaration, name, and assignment. I have explained each one in more detail below.

### Declaration:
As the name suggests, this is where you declare the variable.
 Here, location is important as this provides the computer with context. Context about the scope and the type of information you are looking to store. 
#### Scope
Scope is a tricky topic for newbie coders, even tripping up pro's on occasion. So don't feel disheartened if you find it difficult at first to understand. I plan on writing about this topic in more detail at later date. Until then...
Scope, put in the most simplest of terms. defines which part of the program needs to know about the variable's existence.

If the whole program needs to be aware of the variable, then the scope will be global. This is common for when many functions have use for a variable, but you should avoid this scope if you can. the game as a programmer is to tell the fewest things you need to about the variables you make. 
If only part of the program (e.g. one function) needs to be aware of the variable, then the scope will be local.

    Example:
    You are a barista who is the process of making tea and coffee for customers. 
If you have labeled a spoon for tea and a spoon for coffee, you don't need to tell the customers the labels are exists. It's out of scope of what they need to know. 
 
    Instead, you might want to tell your coworkers as you don't want them to keep using new spoons. as wasting water on washing up, or bring back to computers. excessive use of memory can cause issues for you're program.
 
    Finally, it's closing time and the scope is no longer needed. 
The labels and the spoons should get cleaned up. Most high level languages try to do this for you.

#### Type
There are a lot of languages which have static typed variables. This means you need to tell the computer ahead of time what type of information you are looking to store. 
It also allows the computer memory allocation to prepare space for you.

Think of this as the computer playing a big game of Tetris with your variables. Types tend to boil down to a combination of primitive types. 
You can think of theses as the building blocks of information.

Common data types include:
- text (often referred to as a string)
- number
- true/false (often referred to a boolean)
- binary (other)

In situations where you need to store many values which are in some way associated with each other. many programming languages will allow you to store a group of data within one variable.
 This data does not have to be the same type as each other.

    Returning to our previous coffee shop example. Our baristas have served a lot of customers. Looking into more detail at the collection of customer orders, we can surmise that each order has:
    - a customer
    - the staff member who served them
    - the product(s) ordered.

    The customer and staff gets stored member within the order. represented by their name (i.e. a text value). 
The product(s) also gets stored with in the order, *one person can buy many things, you should see me order doughnuts.*. but should also be a collection within themselves. 
 What I mean by this is that each product will have a name (text), price (number) and quantity (number) associated with it.

#### Name
A variable name provides the text representation or identifier for its stored value.
 It is one of the most important parts of a variable. A wise man once told me that 
     you spend more time thinking of the right name for one variable than you do writing the whole program.
 So, a good variable name will be:
- meaningful
- descriptive
- concise
- contextual
 
A meaningful variable name is difficult to define as it can mean a lot of things depending on the situation. Within a broad content, meaningful refers to a name which readable. It relates to the information a variable stores.

Descriptive names tell you what they store. A descriptive name will also tell you what information the variable does not have.
Concise means keep it brief, keep it short. - you don't want to have to end up writing an essay every time you talk about the variable in your code. *see Java for more information on what not to do.*

Contextual has a lot of overlap with the previous points. The important thing to note here is that 
**plural data types get reserved for collections of the singular thing.**... "customer" should relate a single customer, but "customers" is many. 
Many means a collection or group of, so you shouldn't use it to refer to one customer.
### Value
The information currently attached to the variable. You can change this as many times as you want so long as it matches the expected type, and continues to be true to its name. 