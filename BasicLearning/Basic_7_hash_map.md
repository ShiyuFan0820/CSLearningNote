# Hash Map

## Definition of Hash Map

We know that McDonald's hash browns, which are made with a lot of shredded potatoes, eventually become a evenly distributed pie shape. Hash Map is similar to this one. Hash Map is a data structure that uses a certain hash function to distribute large data evenly across the available storage space, optimizes the access efficiency. 

## How Hash Map Operates

**Operations in Hash Map**

We already know that retrieval elements in an array is by indexing and it's constant time complexity, the principle of how Hash Map operates is also by indexing, it's a key-value loop up. Hash Map uses a certain hash function to compute the key to an index into an array of buckets or slots, the key and value pairs will be stored in one of the buckets associated with the calculated index, when we want to retrieval the key and value, Hash Map will use hash function to convert the key into the index and return the desired key-value pair. If the Hash Map is implemented efficiently, the time complexity for both insertion and retrieval operations can be nearly constant on average, making it a widely used data structure for fast key-value lookups.

**Hashing Algorithm**

Hashing algorithm also known as hash function, it's a calculation applied to a key which may be a very large number or a very long string to transform it into a relatively small index number that corresponds to a position in the Hash Map, this index number is effectively a memory address.

There are many hash functions, like division method, multiplication method, mid-square method, folding method, universal hashing and cryptographic hash functions. Some are more appropriate than others depending on the nature of the data we want to store. 

**Example**

If we want to store keys `3, 4, 5, 21, 18, 45, 20, 6, 96, 11, 24` and their value in a Hash Map whose size is 11, the process is like this:

<div align=center>
<img width="800" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/0ddd4b7a-f371-4ce4-ba59-2b5a85227443">
</div>

Repeat this operation to all keys, we can get a Hash Map with key value pairs:

<div align=center>
<img width="800" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/f2874225-c43b-475c-aec9-9046ae323fb1">
</div>

If we want to retrieval key `24` and its value:

<div align=center>
<img width="800" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/be196ed8-c899-483f-8669-3c288fffe02a">
</div>


## Hash Collision

**What is Hash Collision**

As we use a hash function to calculate the index of a key, there may be cases where the index of two items calculates to be the same, but both items can't be stored in the same bucket, this situation is known as a collision.

**How to Solve Hash Collision**


