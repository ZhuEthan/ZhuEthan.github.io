
GFS (single master), Map-Reduce (single coordinator)

Reading: 

Master: handle -> list of chnkservers, version#, file name -> array of chunkle server -> DISK (LOG, CHECKPOINT)

Client is a lib that has complex logic like combing chunks and etc; 

Writing: 

Client asks Master which chunk to append -> Master needs to designate a primary -> Master needs to find the chunks which have up-to-date replica -> Pick Primary / Secondary -> Increment V# -> Tells P/S V# -> Master writes VN to disk, 

```
Google File System (GFS) is designed for large-scale distributed data storage and is optimized for high fault tolerance and performance. Here's how GFS handles the write process, involving the Master, Primary, and Secondary replicas:

Overview of GFS Write Operation
Client Request: A client initiates the write by sending a request to the GFS Master to identify the locations of the chunk servers that store the replicas of the chunk to be written.

Master Response: The GFS Master responds with the identities and locations of the primary and secondary chunk servers that hold the chunk replicas. It also designates one of the chunk servers as the Primary replica for that specific chunk, while the others are Secondary replicas.

Data Push: The client pushes the data to all replicas (Primary and Secondaries). This data is sent in chunks and buffered in the chunk servers' memory. Importantly, the client does not have to push the data in a particular order, and the chunk servers may receive data at different times.

Write Request to Primary: Once the data has been pushed to all replicas, the client sends a write request to the Primary chunk server. This request specifies the data that should be written and the offset within the chunk where the data should be placed.

Primary Write Operation: The Primary replica writes the data to its own storage and then determines an order for the write operation. It forwards the write request, including the order, to all Secondary replicas to ensure consistency.

Secondaries Acknowledge: Each Secondary replica writes the data as per the specified order and sends an acknowledgment back to the Primary.

Final Acknowledgment to Client: Once the Primary receives acknowledgments from all the Secondary replicas, it sends a final acknowledgment to the client to confirm that the write operation is complete.

Example of a GFS Write Operation
Imagine a client wants to write data "Hello World" to a specific chunk in GFS:

Client Request: The client contacts the GFS Master to get the locations of the chunk servers for the target chunk.
Master Response: The Master returns, saying:
Primary replica: Chunk server A
Secondary replicas: Chunk servers B and C
Data Push: The client pushes the "Hello World" data to chunk servers A, B, and C.
Write Request to Primary: The client sends a write request to chunk server A (the Primary), specifying where to write "Hello World" within the chunk.
Primary Write Operation: Chunk server A writes "Hello World" to its disk and forwards the request, in order, to chunk servers B and C.
Secondaries Acknowledge: Chunk servers B and C perform the write and acknowledge completion back to chunk server A.
Client Confirmation: Once chunk server A receives confirmations from B and C, it sends a final acknowledgment to the client that the write was successful.
This mechanism ensures data consistency and reliability, with the Primary replica coordinating the operation to maintain an ordered, sequential write across all replicas.
```


Lease (To ensure there is no two primary); 

![the-birthday-paradox](../img/The-Birthday-paradox.png)
