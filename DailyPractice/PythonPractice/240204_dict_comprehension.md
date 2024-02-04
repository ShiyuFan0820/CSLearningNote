# Dictionary Comprehension

**Exercise:**

1. Given a sentence `What is the Airspeed Velocity of an Unladen Swallow?`.
2. Use dictionary comprehension to create a dictionary called `result` that takes each word in the given sentence and calculates the number of letters in each word.
3. To keep the exercise simple, count any punctuation following a word with no whitespace as part of the word. For example, `Swallow?` has a length of 8.

**The code is:**
```py
sentence = What is the Airspeed Velocity of an Unladen Swallow?
# Convert the sentence into a list of words.
words_list = sentence.split()
# Use dictonary comprehension to create the result dictionary.
result = {word:len(word) for word in words_list}
print(result)

```

**The output is:**
```py
{'What': 4, 'is': 2, 'the': 3, 'Airspeed': 8, 'Velocity': 8, 'of': 2, 'an': 2, 'Unladen': 7, 'Swallow?': 8}
```
