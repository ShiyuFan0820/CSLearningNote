# CSS

## Style Language

Style sheet language is a language similar to markup language, it's used to specify how things should look in a website. CSS is one kind of style sheet language, which stands for Cascading Style Sheets, there are other style languages like Sass (Syntactically Awesome Style Sheet) Less (Leaner Style Sheet) and so on. 

## How CSS Works?

CSS (Cascading Style Sheets), Cascading refers to the way styles are applied to HTML elements.

There are three different styles of adding CSS, Inline, Internal and External, they are used to define the presentation of HTML elements. Cascading means CSS determine the priority of conflicting styles from these different sources using the cascade, which considers specificity and the other of importance.

**1. Inline**
```
<p style="background: blue;">This is a paragraph with a blue background.</p>
```
As the name suggests, an inline style goes into the same line as a particular HTML element, it's added directly into the opening tag of the HTML element using the `style` attribute.

As the code shows above, the `style` attribute is used within the `<p>` tag to apply CSS styles directly to this paragraph. `background: blue;` is the CSS code, `background` is the property that you want to change, `blue` is the value you what to set the property to.

Inline elements are really useful for adding CSS style to just a single element or specific sections of an HTML document. However, they are not the most efficient way to apply styles if you need to style multiple elements or maintain a consistent design across multiple pages.

**2. Internal**
```
<html>
  <head>
    <style>
      html{
        background: red;
      }
    </style>
  </head>
</html>
```

An internal CSS can go into any element, the html element or the head element, in the example above, it goes into the head element. The structure includes an opening tag` <style>`, and a closing tag` </style>`, in between these tags is where we add all of the CSS, here we need to add an additional selector before a set of curly braces, here the selector is `html`, and the CSS content goes into these curly braces.

Internal CSS styling is usually used for applying it only to one web page.

**3. External**

<div align=center>
<img width="500" alt="image" src="https://github.com/ShiyuFan0820/CSLearningNote/assets/149340606/2c151cff-256c-48a0-a76b-41c0f76dac98">
</div>

The biggest difference between the external, internal and inline styles is that external go to a completely separate file, the file ends with `.css`, in this `.css` file, it also includes a selector, curly braces, the property, and the value. 

To use the `.css` file in the HTML file, we would add a link element which is a self-closing tag, and write a `rel` relationship which refers to what is the role of this thing that it is linking to, and the other one is the `href`, which is the location of the linked file.

External CSS is suitable for multi-page HTML websites.






