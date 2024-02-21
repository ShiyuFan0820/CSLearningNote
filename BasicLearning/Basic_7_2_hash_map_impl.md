**Python**

_Code 1 without solution for collision:_
```py
class HashMap:
    def __init__(self, size, hash_seed):
        self.m_buckets = [None] * size
        self.m_seed = hash_seed

    def hash_key(self, key):
        return key % self.m_seed

    def insert(self, key, value):
        hashed_key = self.hash_key(key)
        if self.m_buckets[hashed_key] != None:
            return RuntimeError(f"Hash collision happened for key {key} and key {self.m_buckets[hashed_key]}.")
        self.m_buckets[hashed_key] = value

    def search(self, key):
        hashed_key = self.hash_key(key)
        searched_value = self.m_buckets(hashed_key)
        print(f"{key}: {searched_value}")


hash_map = HashMap(10, 9)
hash_map.insert(2, "Two")
hash_map.insert(3, "Three")
hash_map.insert(9, "Nine")
hash_map.insert(20, "Twenty")
hash_map.insert(11, "Eleven")
hash_map.insert(57, "Fifty seven")
hash_map.insert(66, "Sixty six")
hash_map.insert(49, "Forty nine")

search_list = [2, 3, 9, 20, 11, 57, 66, 49]
for element in search_list:
    hash_map.search(element)
      
```

_The output is:_
```py
2: Two
3: Three
9: Nine
20: Two
11: Two
57: Three
66: Three
49: Forty nine
```

_Code 2 with solution for collision (Chaining):_
```py
class BucketNode:
    def __init__(self, key, value):
        self.m_key = key
        self.m_value = value
        self.m_next = None


class HashMap:
    def __init__(self, size):
        self.m_size = size
        self.m_buckets = [None] * size

    def hash_key(self, key):
        return key % self.m_size

    def insert(self, key, value):
        hashed_key = self.hash_key(key)
        current_node = self.m_buckets[hashed_key]
        if current_node is None:
            self.m_buckets[hashed_key] = BucketNode(key, value)
            print(f"Insert key-value pair ({key}: {value}) is successful.")
            return
        while current_node.m_next:
            current_node = current.m_next
        current_node.m_next = BucketNode(key, value)
        print(f"Insert key-value pair ({key}: {value}) is successful.")

    def delete(self, key):
        hashed_key = self.hash_key(key)
        current_node = self.m_buckets[hashed_key]
        prev_node = None
        while current_node:
            if current_node.m_key == key:
                if prev_node:
                    prev_node.m_next = current_node.m_next
                    print(f"Key-value pair ({current_node.m_key}: {current_node.m_value}) deleted.")
                    return
                else:
                    self.m_buckets[hashed_key] = current_node.m_next
                    print(f"Key-value pair ({current_node.m_key}: {current_node.m_value}) deleted.")
                    return
            prev_node = current_node
            current_node = current_node.m_next
        print(f"Key {key} not exist.")

    def search(self, key):
        hashed_key = self.hash_key(key)
        current_node = self.m_buckets[hashed_key]
        while current_node:
            if current_node.m_key == key:
                print(f"{current_node.m_key}: {current_node.m_value}.")
                return
            current_node = current_node.m_next
        print(f"key {key} not exist.")


hash_map = HashMap(11)
hash_map.insert(20, "twenty")
hash_map.insert(9, "nine")
hash_map.insert(1, "one")

hash_map.search(20)
hash_map.search(9)
hash_map.search(31)
hash_map.search(2)

hash_map.delete(9)
hash_map.delete(10)

hash_map.search(9)
   
```


