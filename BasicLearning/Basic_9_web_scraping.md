# Web Scraping

Some websites can be accessed with their API. However, some websites don't have an API, or their API doesn't let us do all the things that we want to do. So we can use web scraping to look through the underlying HTML code of a website to get hold of the information that we want.

## Module BeautifulSoup

Beautiful Soup is a Python library for pulling data out of HTML and XML files.

To use BeautifulSoup, we should install package `bs4` first, and import `BeautifulSoup` class.

To create a BeautifulSoup object (often referred to as making the "Soup"), two main arguments are required, one is the HTML or XML document, the other one is the parser type, and this can help `BeautifulSoup` understand the contents of the document. The HTML parser is `html.parser`, the XML parser needs install the `lxml` package first, and pass in `lxml` in the class. 

Once we have a BeautifulSoup object, we can use its methods and attributes to navigate and manipulate the document's elements.

BeautifulSoup simplifies the process of scraping and parsing web data, making it easier to extract specific information from HTML and XML documents using Python.
