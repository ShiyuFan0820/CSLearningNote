# Error Handling

**Exercise 1: IndexError Handling**

1. Given a buggy code, there will be an index error if you run the code directly.
2. Modify the code, prevent it from crashing.
3. If the index is out of range, the final output should be "Fruit pie".

The given buggy code:
```py
fruits = ["Apple", "Orange", "Peach"]


def make_pie(Index):
  fruit = fruits[Index]
  pirnt(fruit + " pie")


make_pie(4)
```

Modified code:
```py
fruits = ["Apple", "Orange", "Peach"]


def make_pie(Index):
  try:
    fruit = fruits[Index]
  except IndexError:
    print("Fruit pie")
  else:
    pirnt(fruit + " pie")


make_pie(4)
```

**Exercise 2: KeyError Handling**

1. Given a list of dictionaries of facebook posts' "Likes", "Commends" and "Shares" information.
2. Given a buggy code to collect the number of "Likes".
3. When run the code, there is a KeyError because some of the posts don't have "Likes".
4. Use exception handling to prevent the program from crashing.

The given buggy code:
```py
facebook_posts = [{'Likes': 21, 'Comments': 2}, {'Likes': 13, 'Comments': 2, 'Shares': 1}, {'Likes': 33, 'Comments': 8, 'Shares': 3}, {'Comments': 4, 'Shares': 2},{'Comments': 1, 'Shares': 1}, {'Likes': 19, 'Comments': 3}]
total_likes = 0
for post in facebook_posts:
  total_likes = total_likes + post['Likes']
print(total_likes)
```

Modified code:
```py
facebook_posts = [{'Likes': 21, 'Comments': 2}, {'Likes': 13, 'Comments': 2, 'Shares': 1}, {'Likes': 33, 'Comments': 8, 'Shares': 3}, {'Comments': 4, 'Shares': 2},{'Comments': 1, 'Shares': 1}, {'Likes': 19, 'Comments': 3}]
total_likes = 0
for post in facebook_posts:
  try:
    total_likes = total_likes + post['Likes']
  except:
    pass
print(total_likes)
```
