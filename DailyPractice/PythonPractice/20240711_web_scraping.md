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

2. It's found that all the article names and links are written in an anchor tag under a `<span>` element.

<div align=center>
<img width="650" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/df02ea4b-0ca3-479c-81bf-b620b82d412f">
</div>










