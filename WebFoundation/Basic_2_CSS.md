# CSS

## Style Language

Style sheet language is a language similar to markup language, it's used to specify how things should look in a website. CSS is one kind of style sheet language, which stands for Cascading Style Sheets, there are other style languages like Sass (Syntactically Awesome Style Sheet) Less (Leaner Style Sheet) and so on. 

## How CSS Works?

CSS (Cascading Style Sheets), Cascading refers to the way styles are applied to HTML elements.

There are three different styles of adding CSS, Inline, Internal and External, they are used to define the presentation of HTML elements. Cascading means CSS determine the priority of conflicting styles from these different sources using the cascade, which considers specificity and the other of importance.

**1. Inline**
```
<html style="background: blue">
</html>
```
As the name suggests, it goes into the same line as a particular HTML element, as the code shows above, it goes into the opening tag of the HTML. `background: blue` This part is the CSS code, the first part of it is the property that you want to change, here it's the `background`, the second part is the value of that property you want to set it to, here it sets the background to `blue`.

Inline elements are really useful for adding CSS style to just a single element or specific sections.

**2. Internal**
```
<html>
    <head>
        <style>
            html{
              background: read;
            }
        </style>
    </head>
</html>
```

An internal CSS can go into any element, the html element or the head element, in the example above, it goes into the head element. The structure includes an opening tag` <style>`, and a closing tag` </style>`, in between these tags is where we add all of the CSS, here we need to add an additional selector before a set of curly braces, here the selector is `html`, and the CSS content goes into these curly braces.

Internal CSS styling is also usually used for applying it only to one HTML document.

**3. External**









