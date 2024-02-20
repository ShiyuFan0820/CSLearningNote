# Hash Map

## Definition of Hash Map

We know that McDonald's hash browns, which are made with a lot of shredded potatoes, eventually become a evenly distributed pie shape. Hash Map is similar to this one. Hash Map is a data structure that uses a certain hash function to distribute large data evenly across the available storage space, optimizes the access efficiency. 

## How Hash Map Operates

We already know that retrieval elements in an array is by indexing and it's constant time complexity, the principle of how Hash Map operates is also by indexing, it's a key-value loop up. Hash Map uses a certain hash function to compute the key to an index into an array of buckets or slots, the key and value pairs will be stored in one of the buckets associated with the calculated index, when we want to retrieval the key and value, Hash Map will use hash function to convert the key into the index and return the desired key-value pair. If the Hash Map is implemented efficiently, the time complexity for both insertion and retrieval operations can be nearly constant on average, making it a widely used data structure for fast key-value lookups.

## Hashing Algorithm

**Definition of Hashing Algorithm**

Hashing algorithm also known as hash function, it's a calculation applied to a key which may be a very large number or a very long string to transform it into a relatively small index number that corresponds to a position in the Hash Map, this index number is effectively a memory address.

**Types of Hashing Algorithm**

There are many hash functions, like division method, multiplication method, mid-square method, folding method, universal hashing and cryptographic hash functions. Some are more appropriate than others depending on the nature of the data we want to store. 

## Hash Collision

As we use a hash function to calculate the index of a key, there may be cases where the index of two keys calculates to be the same, but both this situation is known as a collision.

## How to Solve Hash Collision
