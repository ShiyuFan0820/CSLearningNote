 # Scraping a Live Website

1. Given website [Hacker News](https://news.ycombinator.com/news).
2. Using BeautifulSoup to scrap the latest article with the most points, print the total points, article name, and link.

**Solution**

1. Open the website link, right-click on the page, and select the `Inspect` option to open the HTML.

<div align=center>
<img width="300" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/caa598ec-6ef4-4ffe-8242-aac5438266c7">
</div>

<div align=center>
<img width="650" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/0757ec5f-d233-4c08-8597-998bde23a506">
</div>

2. It's found that all the article names and links are written in an anchor tag under a `<span>` element with the class name `titleline`.

<div align=center>
<img width="650" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/df02ea4b-0ca3-479c-81bf-b620b82d412f">
</div>

3. All points are also written in a `<span> element with the class name `score`.

<div align=center>
<img width="650" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/76f749ce-de1e-494a-9b75-4a1ffd28bd35">
</div>

4. The code is:
```
from bs4 import BeautifulSoup
import requests

response = requests.get("https://news.ycombinator.com/news")

# Get the HTML of the website.
yc_web_page = response.text

soup = BeautifulSoup(yc_web_page, "html.parser")

article_texts = []
article_links = []
article_points = []

# Extract the links and names.
articles = soup.find_all(name="span", class_="titleline")
for article in articles:
    link = article.find('a')
    if link:
        text = link.text
        article_texts.append(text)
        href = link.get('href')
        article_links.append(href)

# Extract the points.
score_texts = soup.find_all(name="span", class_="score")
article_upvotes = [int(score.getText().split()[0]) for score in score_texts]
largest_number = max(article_upvotes)
largest_index = article_upvotes.index(largest_number)
print(f"The largest points is {largest_number}, the article is {article_texts[largest_index]}, the link is {article_links[largest_index]}.")

```








