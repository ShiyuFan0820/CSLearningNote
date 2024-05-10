# HTML
Most modern websites are created using HTML, CSS, and Javascript, and HTML is the only one that can be displayed as a web page on its own.

HTML stands for Hypertext Markup Language. It is the standard markup language for creating web pages and web applications. It's like the skeleton of a web page.

Hypertext refers to the pieces of text which can link to other documents in the website, these pieces of text are hypertext or hyperlinks. Markup Language means HTML uses tags to mark up or define different parts of a web page. These tags provide instructions to web browsers about how to display the content. The tags of HTML are often written between `<>`.

The HTML elements are a combination of an opening tag and a closing tag and content between them.

## Heading Element

When writing the heading element, it starts with an opening tag `<h1>` and ends with a closing tag `</h1>`, the text content is between the opening and closing tag. There are 6 hierarchies of headlines in total, the advantage of using this is that it can automatically generate directories. Remember, do not have more than one h1 in the code, and do not skip a level, such as don't go straight from h1 to h3.

For example:
```
<h1>Heading 1</h1>
<h2>Heading 2</h2>
<h3>Heading 3</h3>
<h4>Heading 4</h4>
<h5>Heading 5</h5>
<h6>Heading 6</h6>
```

It will be displayed like this:

<div align=center>
<img width="300" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/ce8738e6-2ba6-4e22-a611-8476ec51ac61">
</div>

## Paragraph Element

The opening tag for the paragraph element is `<p>`, and the closing tag is </p>. This will separate two paragraphs.

For example:
```
<p>This is a paragraph.</p>
<p>This is another paragraph.</p>
```

It will be displayed like this:

<div align=center>
<img width="300" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/2b7d2fd0-5f83-457d-ad87-c65bd9cd2ac7">
</div>

## Void Element

A void element is an element where you are forbidden from putting any content inside the tag.

1. Horizontal Rule Element `<hr />` (`<hr>` also works), use this element between two elements, it will create a line between them.

For example:
```
<p>This is a paragraph.</p>
<hr />
<p>This is another paragraph.</p>
```

It will be displayed like this:

 <div align=center>
<img width="300" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/d603c5a1-14a5-4bfd-80ed-340ab45d1d47">
 </div>

2. Break Element `<br />` (`<be>` also works), use this element in a paragraph will wrap everything after the element.

For example:
```
<p>This is a paragraph. I need to wrap the paragraph in the next sentence.<br /> This is the wrapped sentence.
```

It will be displayed like this:
<div align=center>
<img width="483" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/d1e4f6f8-7060-40bb-befc-3a63108b6311">
</div>

## Boilerplate

A Boilerplate is a basic template structure of the HTML file, the basic structure is like this:
```
<!DOCTYPE html> <!--This tag tells the brower which version of HTML the file was written in.-->
<html lang="en"> <!--This is the root of the HTML file, all elements are going to write inside of this tag. lang means language, if you use a website speaker to read the website, they will check the targeted language to read.-->
  <head> <!--This is the area where important information about the website is placed, the things included in here help the website render in the brower correctly, and will not be displayed to the user.-->
    <meta charset="UTF-8"> <!--This ensures the characters that you're using on your website gets displayed correctly.-->
    <title>My Website</title> <!--The title here is the name of the website usually gets displayed up in the tab bar.-->
  </head>

  <body> <!--Here is where all of the content of the website displayed.-->
    <h1>This is the body of My Website</h1>


  </body>
</html>
```

It will be displayed like this:

<div align=center>
<img width="500" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/fedf3a86-9e72-434e-8ae4-df39731e1ef7">
</div>

## List Element

**Unordered List**

Unordered lists are the lists that start after a dot.

The structure is:
```
<ul>
    <li>List element 1</li>
    <li>List element 2</li>
    <li>List element 3</li>
</ul>
```

It will be displayed like this:

<div align=center>
<img width="200" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/59d9dc65-a254-4445-a238-a46a166dae8d">
</div>

**Ordered List**

Ordered lists are numbered lists.

The structure is:
```
<ol>
    <li>List element 1</li>
    <li>List element 2</li>
    <li>List element 3</li>
</ol>
```

It will be displayed like this:

<div align=center>
<img width="180" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/f3911755-e277-430e-9f2b-041354455f5e">
</div>

## Anchor Element

Anchor element can be used to create hyperlinks, the opening tag is `<a>`, and the closing tag is `</a>`. The link goes into the part just after the `a` of the opening tag, and follows an attribute `href=`, the name of the link can be write between the opening and closing tags.

For example:
```

```













