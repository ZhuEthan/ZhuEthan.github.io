It has been almost two months since I left US Amazon for visa issue. Still waiting for my CA visa. During this precious temporary leaving time, I decided to review my knowledge of computer architecture. Here I demonstrated the lab malloc since it may involve some designs and several iterations. I will list the stages one by one below

#### Implicit linked list: 
The implicit linked list is the easiest implementation of malloc, the underground data structure is an array of memory. The memory is split into many blocks bounded by size/allocation bits. The allocation bit could be 0 or 1, 0 represents the related block is free and 1 represents not free. Whenever a given size consecutive memory is requested (malloc), a free block will be filtered out from the whole implicit linked list and be marked as allocated with the requested size. In the same way, the free request will claim back the already allocated memory. The overall structure of implicit memory list is as below: 

![implicit linked list](https://github.com/ZhuEthan/ZhuEthan.github.io/blob/master/img/implicit-linked-list.png)


