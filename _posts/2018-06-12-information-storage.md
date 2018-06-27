---
layout: post
title: "Counting bits set, bitCount"
date: 2018-06-17
excerpt: "CSAPP3e Self-Study Datalab"
tags: [CSAPP, Computer Systems]
---

# Representing and Manipulating Information

## Information Storage

- The product of a set of positive numbers will always be positive, although overflow will yield the special value to $+\infty$.  
- Floating-point arithmetic is not associative due to the finite precision of the representation.


> **The role of pointers in C**
> 
> They provide the mechanism for referencing elements of data structures including arrays. Pointers has two aspects: *value* and *type*. The value indicates the location of some object,


### Hexadecimal Notation

<div style="text-align:center">
  <img src ="https://cdn-images-1.medium.com/max/405/1*DbVq0VMJDZYKbYmNZMM0hg.jpeg" width="60%"/>
  <p><strong>Fig 2.2 Hexadecimal notation</strong>. Each hex digit encodes one of 16 values. </p>
</div>


One simple trick for doing the conversion in your head is to memorize the decimal equivalents of hex digits A, C, and F. Then the hex values B, D, and E can be translated to decimal by computing their values relative to the first three.


### Data Sizes

Every computer has a *word size*, indicatipg the nominal size of pointer data. Since a *virtual address* is encoded by such a word, the most important system parameter determined by the word size is the _maximum size of the virtual address space_. That is, for a machine with a w-bit word size, the virtual addresses can range from 0 to $2^w - 1$, giving the program access to at most $2^w$ bytes.

- Integer data can be either *signed*, able to represent negative; zero, and positive values, or *unsigned*, only allowing nonnegative values. 
- Data type `char` represents a single byte. Although the name char derives from the fact that it is used to store a single character in a text string, it can also be used to store integer values

Data types `short`, `int`, and `long` are intended-to provide a range of sizes. Even when compiled for 64-bit systems, data type int is usually just 4 bytes. Data type long commonly has 4 bytes in 32-bit programs and 8 bytes in 64-bit programs.


### Addressing and Byte Ordering

- The former convention - where the *least significant byte comes first* is referred to as `little-endian`.
- The latter convention - where the *most significant byte comes first* is referred to as `big-endian`.

Suppose the variable `x` of type int and at address `0x100` has a hexadecimal value of `0x01234567`. The ordering of the bytes within the address range `0x100` through `0x103` depends on the type of machine:

<div style="text-align:center">
  <img src ="http://4.bp.blogspot.com/_IEmaCFe3y9g/SO3GGEF4UkI/AAAAAAAAAAc/z7waF2Lwg0s/s400/lb.GIF" width="60%" />
  <p><strong>Fig 2.3 big-endian and little-endian</strong>. </p>
</div>


### 2.1.4 Representing Strings

A string in C is encoded by an array of characters terminated by the `null` (having value O) character. Each character is represented by some standard encoding, with the most common being the ASCII character code. Thus, if we run our routine show _bytes with arguments "12345" and 6 (to include the terminating character), we get the result `3132 33 34 35 00`

> **A fundamental concept of computer systems is that a program, from the perspective of the machine, is simplfa sequence of bytes.**



### 2.1.6 Introduction to Boolean Algebra

<div style="text-align:center">
  <img src ="http://engineeronadisk.com/book_analysis/images/boolean9.gif" width="60%" />
  <p><strong>Figure 2.7 Operations of Boolean algebra</strong>. Binary values 1 and 0 encode logic values TRUE and FALSE, while operations ~, &, |, and ^ encode logical operations NOT, AND, OR, and EXCLUSIVE-OR, respectively.
</p>
</div>


### 2.1.7 Bit-Level Operations in C

C supports bitwise Boolean operations. In fact, the symbols we have used for the Boolean operations are exactly those used by C: `|` for `OR`, `&` for `AND`, `~` for `NOT`, and `^` for `EXCLUSIVE-OR`.


### 2.1.8 Logical Operations in C

C also provides a set of *logical operators* `||`, `&&`, and `!`, which correspond to the `OR`, `AND`, and `NOT` operations of logic.


### 2.1.9  Shift Operations in C

In contrast to C, Java has a precise definition of how right shifts should be performed. The expression `x >> k` shifts x arithmetically by k positions, while `x >>> k` shifts it logically.


<div style="text-align:center">
  <img src ="http://slideplayer.com/5178537/16/images/2/Logical+vs+Arithmetic+Shifts.jpg" width="60%" />
  <p><strong>Figure 2.8 logical and arithmetic shift in c</strong>. </p>
</div>


For unsinged data, right shifts must be logical.
Mostly using logical shift when singed data.


> Shifting by k, for large values of k
> 
> For a type consisting of w bits, what shohld be the effect of shifting by some value $k \geq w$ ? 
> 
> The shift amount is computed as k mod w.

## References
  
[1] Randal E. Bryant, David R. O'Hallaron, Carnegie Mellon University [*"
Computer Systems: A Programmer's Perspective, 3/E (CS:APP3e)"*](http://csapp.cs.cmu.edu/3e/labs.html)  
[2] Randal E. Bryant, David R. O'Hallaron [*"Computer Systems: A Programmer's Perspective (3rd Edition)"*](https://www.amazon.com/Computer-Systems-Programmers-Perspective-3rd/dp/013409266X)