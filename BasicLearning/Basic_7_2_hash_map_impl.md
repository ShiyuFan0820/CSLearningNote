**Python**

_Code 1 (Without solution for collision):_
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

hash_map.search(2)
      
```

_The output is:_
```py
line 17, in search
    searched_value = self.m_buckets(hashed_key)
                     ^^^^^^^^^^^^^^^^^^^^^^^^^^
TypeError: 'list' object is not callable
```




