---
layout: post
title: MallocLab In CSAPP
tags: [CS, System]
ext-js: "https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML
---

It has been almost two months since I left US Amazon for visa issue. Still waiting for my CA visa. During this precious temporary leaving time, I decided to review my knowledge of computer architecture. Here I demonstrated the lab malloc since it may involve some designs and several iterations. I will list the stages one by one below

#### Implicit linked list: 
The implicit linked list is the easiest implementation of malloc, the underground data structure is an array of memory. The memory is split into many blocks bounded by size/allocation bits. The allocation bit could be 0 or 1, 0 represents the related block is free and 1 represents not free. Whenever a given size consecutive memory is requested (malloc), a free block will be filtered out from the whole implicit linked list and be marked as allocated with the requested size. In the same way, the free request will claim back the already allocated memory. The overall structure of implicit memory list is as below: 

![implicit linked list](https://github.com/ZhuEthan/ZhuEthan.github.io/blob/master/img/implicit-linked-list.png) image 1


The hdr(header) and ftr(foot) in the image 1 contains identical info: size and allocation status. The size info includes both the size of data and the size of foot&header, thus a pointer referring to a data block plus size indicated in head / foot will point to the starting point of the next data block. Both header and foot existing though including the same info will benefit forward traversal and reverse traversal. 

With math notation to represent all relations above: 

```
#define GET_SIZE(p) (GET(p) & ~0x7)

#define GET_ALLOC(p) (GET(p) & 0x1)

// Given data block ptr bp, compute address of its header and footer

#define HDRP(bp) ((char*)(bp) - WSIZE)

#define FTRP(bp) ((char*)(bp) + GET_SIZE(HDRP(bp)) - DSIZE)

// Given data block ptr bp, compute address of next and pre blocks

#define NEXT_BLKP(bp) ((char*)(bp) + GET_SIZE(((char*)(bp) - WSIZE)))

#define PREV_BLKP(bp) ((char*)(bp) - GET_SIZE(((char*)(bp) - DSIZE)))$$
```
