---
layout: post
title: MallocLab In CSAPP
tags: [CS, System]
ext-js: "https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML"
---


It has been two months since I left US Amazon for visa issue. Still waiting for my CA visa. During the temporary leaving time, I decided to review my knowledge of computer architecture. Here I demonstrated the lab malloc as it involves some design thinking. Stages are listed one by one as below

#### Implicit linked list: 
The implicit linked list is the easiest implementation of malloc, the underground data structure is an array of memory. The memory is split into blocks bounded by hdr and ftr accomodating size/allocation bits. The allocation bit could be 0 or 1, 0 represents the related block is free and 1 represents not free. The size bit is just the binary number representing the size of the related block. Whenever a given size consecutive memory is requested (malloc), a free block will be filtered out from the whole implicit linked list and be marked as allocated with the requested size. In a similar way, the free request will claim back the already allocated memory (change the allocation bit back to 0). The overall structure of implicit memory list is as below: 

![implicit linked list](../img/implicit-linked-list.png)
image 1


The hdr(header) and ftr(foot) in the image 1 contains identical info: size and allocation status. The size is the sum of the size of data and tha of foot&header. A pointer referring to a data block plus size in header / foot will point to the starting point of the next data block. Both header and foot existing will benefit forward traversal and reverse traversal. 

With math notation to represent all relations above: 

```
#define GET_SIZE(p) (GET(p) & ~0x7)
#define GET_ALLOC(p) (GET(p) & 0x1)
// Given data block ptr bp, compute address of its header and footer
#define HDRP(bp) ((char*)(bp) - WSIZE)
#define FTRP(bp) ((char*)(bp) + GET_SIZE(HDRP(bp)) - DSIZE)
// Given data block ptr bp, compute address of next and pre blocks
#define NEXT_BLKP(bp) ((char*)(bp) + GET_SIZE(((char*)(bp) - WSIZE)))
#define PREV_BLKP(bp) ((char*)(bp) - GET_SIZE(((char*)(bp) - DSIZE)))
```
The result util and throughput result for this method is as below: 

![implicit linked list](../img/implicit-linked-list-result.png)

#### Improved implicit linked list: 
In the implicit linked list, identical info including size/allocation status is stored twice in both header and foot. Is there any way to reduce this duplication? As this info stored in the foot is to improve simplicity when reverse traversing the linked list, we could remove this duplication for blocks no reverse traversing is needed. It is worth noticing that reverse traversing only happenes when the prev block is free and coalesce needs to be happening. Thus, the foot block could be removed when the prev block is malloced. In order to know whether prev block has been allocated or not without foot info, an extra bit is being stored in the header (thinking header was storing size | cur-alloc) so that header turns into size | cur-alloc | prev-alloc. With the extra prev-alloc info, reverse traversing could decide the existence of the foot in the prev block. 

The final util scores increase from 81% to 82% with this improvement. 



