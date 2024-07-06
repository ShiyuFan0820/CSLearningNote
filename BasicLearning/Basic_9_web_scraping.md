# Web Scraping

Some websites can be accessed with their API. However, some websites don't have an API, or their API doesn't let us do all the things that we want to do. So we can use web scraping to look through the underlying HTML code of a website to get hold of the information that we want.

## Module BeautifulSoup

Beautiful Soup is a Python library for pulling data out of HTML and XML files.

To use BeautifulSoup, we should install package `bs4` first, and import `BeautifulSoup`.

To make the "Soup", we should use `BeautifulSoup` class, pass in the document (HTML or XML), and the parser, passing in the parser is to tell the BeautifulSoup the document is HTML or XML, and this can help `BeautifulSoup` understand the contents of the document. The HTML parser is `html.parser`, the XML parser 
