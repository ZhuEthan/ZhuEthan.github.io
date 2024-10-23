
GFS (single master), Map-Reduce (single coordinator)

Reading: 

Master: handle -> list of chnkservers, version#, file name -> array of chunkle server -> DISK (LOG, CHECKPOINT)

Client is a lib that has complex logic like combing chunks and etc; 

Writing: 

Client asks Master which chunk to append -> Master needs to designate a primary -> Master needs to find the chunks which have up-to-date replica -> Pick Primary / Secondary -> Increment V# -> Tells P/S V# 


![the-birthday-paradox](../img/The-Birthday-paradox.png)
