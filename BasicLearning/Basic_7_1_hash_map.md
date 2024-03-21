# Hash Map

## Definition of Hash Map

We know that McDonald's hash browns, which are made with a lot of shredded potatoes, eventually become a evenly distributed pie shape. Hash Map is similar to this one. Hash Map is a data structure that uses a certain hash function to distribute large data evenly across the available storage space, optimizes the access efficiency. 

## How Hash Map Works?

We already know that retrieval elements in an array is by indexing and it's constant time complexity, the principle of how Hash Map works is also by indexing, it's a key-value look up. Hash Map uses a certain hash function to compute the key to an index into an array of buckets or slots, the key and value pairs will be stored in one of the buckets associated with the calculated index, when we want to retrieval the key and value, Hash Map will use hash function to convert the key into the index and return the desired key-value pair. If the Hash Map is implemented efficiently, the time complexity for both insertion and retrieval operations can be nearly constant on average, making it a widely used data structure for fast key-value lookups.

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

As we use a hash function to calculate the index of a key, there maybe cases where the index of two items calculates to be the same, but both items can't be stored in the same bucket, this situation is known as a hash collision.

**How to Solve Hash Collision?**

1. Open address.

Resolving a collision by placing an item somewhere other than it's calculated address is called open address, cause every bucket/location is open to any item. We can simply add a value to the calculated index, or we can square the calculated index, or by other algorithm, when we want to do searching we also retrieve by the algorithm. 

<div align=center>
<img width="750" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/79ab7e81-b5d5-4d4e-891f-2981d04389a9">
</div>

Advantage: Open address is simple to implement and requires less memory overhead as it does not involve storing additional pointers for linked list.

Disadvantage: Result in clustering, because keys might bunch together inside the array while large proportions of it remains unoccupied, and open addressing may encounter difficulties when the Hash Map becomes densely populated, as finding an empty bucket to resolve a collision can become increasingly challenging and resizing an open-addressed Hash Map can be complex, once the size is ran out, the Hash Map would crash.

2. Chaining

Instead of storing elements directly in an alternative buckets, chaining involves storing multiple key-value pairs by using a linked list or other data structures at each bucket. When we want to do searching we just traverse the linked structures to find the desired element.

<div align=center>
<img width="705" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/dd9c9f64-cfa7-48bb-a947-05726491dc8d">
</div>

Advantage: Chaining provide a flexible approach to handle collisions, ensuring that the Hash Map remains stability even when the number of collisions increases. By using linked list to store colliding key-value pairs, chaining allows for dynamic resizing of the Hash Map without risking a crash due to excessive collisions

Diadvantage: Chaining requires additional memory to store the linked lists, which can lead to increased memory useage, especially if many collisions occur, and this would also degrade the efficiency of search elements to O(n) complexity.

3. Control load factor within a range.

Load factor in a Hash Map is the ratio of the number of elements stored in the Hash Map to the total number of buckets, it indicates how full the Hash Map is and can affect its performance, the load factor best under 70%.

Overall, the main goal of a Hash Map is to choose a suitable hash function to maximize randomness of index and produce the least amount of collisions.


