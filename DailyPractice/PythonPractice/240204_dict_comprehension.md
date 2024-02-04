# Dictionary Comprehension

**Exercise 1:**

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

**Exercise 2:**

1. Given a dictionary called `weather_c = {"Monday": 12, "Tuesday": 14, "Wednesday": 15, "Thursday": 14, "Friday": 21, "Saturday": 22, "Sunday": 24}`.
2. Use dictionary comprehension to create a dictionary called `weather_f` that takes each temperature in degrees Celsius and converts it into degrees Gahrenheit.
3. To convert temp_c into temp_f use this formula: `(temp_c * 9/5) + 32 = temp_f`.

**The code is:**
```py
weather_c = {"Monday": 12, "Tuesday": 14, "Wednesday": 15, "Thursday": 14, "Friday": 21, "Saturday": 22, "Sunday": 24}
weather_f = {day:(temp_c * 9/5) + 32 for (day, temp_c) in weather_c.items()}
print(weather_f)

```

**The output is:**
```py
{'Monday': 53.6, 'Tuesday': 57.2, 'Wednesday': 59.0, 'Thursday': 57.2, 'Friday': 69.8, 'Saturday': 71.6, 'Sunday': 75.2}
```
