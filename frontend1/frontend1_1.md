HTML (HyperText Markup Language) is the most basic building block of the Web. It defines the skeleton, the structure of webpages. What elements are present, how they are related to each other, their hierarchy.

CSS (Cascading Style Sheets) is the skin and clothes. It makes it looks nice, presentable.

Lastly, JS (JavaScript) is the nervous system, the brain; or alternatively the muscles of a webpage. It remembers, communicates, makes elements move around and responds to events like clicks or form submissions.

![htmlmeme](https://i.imgur.com/BYE0mms.png)

These three - in addition to various media types, like images, music, videos or other documents - are all that a web browser can handle.

You may develop a web application with PHP, Python, TypeScript ([or even Scheme](https://homes.cs.aau.dk/~normark/laml-distributions/laml/info/laml-motivation.html)), in the end when you open a webpage it will be HTML page, with optional CSS styling and JavaScript.

# 1. HTML

## 1.1 elements

HTML is made of various elements.
An element can further deconstructed into opening and closing tags and its contents.

In this example, we use a header with the text "i love cats...". In the browser it will appear big and bold.
```
<h1> i love cats i love cats i love cats </h1>
 
 ^ opening tag       ^ content            ^ closing tag 
```

> It will by default appear bigger and bolder than regular text, but we will learn, that any styling can be easily overwritten.

An element can also be self-closing if it does not have a closing tag. Such can be the case with an image inserted into the page or a linebreak. In this case, the end of the tag have a ```/``` sign as you can see below.

```
<br />
```

## 1.2 attributes

Attributes add extra information to an element. Like a unique identifier, name, CSS classes or many others...
An attribute has a name and a value. In the case of logical (boolean) attributes with only true-false values, the value can be left out.
These have to be adeed on the opening tag delimited with spaces.

Here, the ```src``` and ```alt``` and ```disabled``` are attributes, while ```https://http.cat/100.jpg``` and ```a picture of a cat``` are values. ```disabled``` is also a boolean attribute (it is either disabled or not) sot its value can be left out.

```
<img src="https://http.cat/100.jpg" alt="a picture of a cat" />

<button disabled> You can not click me!</button>
```

The most common attributes are:

```id```: The unique identifier of an element. It is most commonly used by JavaScript to manipulate or get values from various elements.

```class```: Similar to ID, but it should not be unique, numerous elements can have the same classes, and an element can have multiple classes as well.

```style```: Apply a CSS style directly to the element. Unadvised, we will see better ways to achieve the same.

Below you can see an example of these attributes in action:

```
<p id="my-paragraph" class="bg-dark text-light custom-shadows" style="font-size: 15px;">
```

## 1.3 block and inline elements

An element can be either a block level or inline.

### Block elements:
- always appear in a new line
- can only be put inside another block level element

Examples of block-level elements are paragraphs, lists, navigation or footer menus :

 ```
<p>This is a text</p>

<ul>
    <li>Menu element 1</li>
    <li>Menu element 2</li>
</ul>

<footer> this is the footer of the webpage </footer>
```

### Inline elements:
- in the browser, they appear in the same line as the previous element, right after it
- can be part of the content a block level element

Examples are links, images, input elements or inline text containers:

```
<a href="#">This is a link to nowhere</a>

<img src="https://http.cat/200.jpg" />

<input type="date" />

some text <span style="color: red;"> with some parts in red </span> some other text
```

Let's see an example of embedding elements into each other:
We will use the ```div``` content division element as the parent block element, and put block as well as inline elements into it:

```
<div>
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. In ac vulputate ligula. <span style="background-color:yellow">Integer tortor velit</span>, suscipit id scelerisque non, convallis vel neque. Ut sagittis dui ut dignissim venenatis.
</div>
<hr/>
<div>
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. In ac vulputate ligula. <p style="background-color:yellow">Integer tortor velit</p>, suscipit id scelerisque non, convallis vel neque. Ut sagittis dui ut dignissim venenatis.
</div>
```

![blockinline](https://i.imgur.com/YAKT4al.png)

We can clearly see, that a ```span``` does not break the flow of its parent, while a ```p``` does by starting strictly at a new line.


## 1.4 HTML standards and stucture

HTML is **very** tolerant as to what is syntactically allowed and what will or will not work.

### 1.4.1 HTML template

A boilerplate HTML "template" can be the following:

```
<!DOCTYPE html>
<html lang="en">
    <head>
        <!--... some stuff here ... -->
        <title>My first website</title>
    </head>
    <body>
        <!--... some stuff here ... -->
    </body>
</html>
```

In the first line we declare the version of HTML standard that we use. Our example tells the browser to treat the site as HTML5. 

The second line is the opening starter ```<html>``` tag which is the root element of a page; inside it, the ```lang``` specifies the main language of texts used in the page.

In the head we can define various metadata ```<head>``` that are invisible to the user. It most notably contains information to search engines, character encoding and viewport settings and linked resources like JavaScripts, Stylesheets, fonts and so on. 
It also hosts the ```title``` tag which is the small text appearing on the top of the web browser on the tabs.

Lastly, the ```body``` hosts the content of the website.

> Once again, HTML is **VERY** flexible of what it allows. You can experiment which elements or tags can be removed - however keep in mind that it will work in *most cases*, therefore you might encounter situations where leaving out a specific element, or a wrong order can cause weird issues which are pretty hard to debug.

### 1.4.2 body template

Contents of the body can be further deconstructed into building blocks [semantically](https://developer.mozilla.org/en-US/docs/Glossary/Semantics#semantic_elements):

```
<!DOCTYPE html>
<html>
    <body>
        <header>
            title
            <nav>
                menu elements
            </nav>
        </header>
        <main>
            <section>
                main section
                <article>
                    first text content
                </article>
            </section>
            <aside>
                sidebar
            </aside>
        </main>
        <footer>
            footer
        </footer>
    </body>
</html>
```

```<header>``` is well.. the header of the page or a section containing menus, title, possibly search bar or settings as well.

The ```<nav>``` element signifies that it will contain navigation links to sections or other pages, sites.

```<aside>``` can be some sidebar with no relation to the main section

Main (```<main>```) is the dominant content, the core of the page contents.

```<section>``` is a generic standalone section of a document, can be very similar
to the ```<article>``` which is a smaller self-contained composite element in a page: like a news article, or a comment or blogpost on a forum.

Lastly, the ```<footer>``` is the bottom of the page usually with hyperlinks, sitemap or contact information.

> If we were to put all of these into a webpage, the result would look something like the following figure

![semantic1](https://i.imgur.com/DujEsNC.png)

Which would be for human eyes virtually undistinguishable from the following: 

```
<!DOCTYPE html>
<html>
    <body>
        <div>
            title
            <div>
                menu elements
            </div>
        </div>
        <div>
            <div>
                main section
                <div>
                    first text content
                </div>
            </div>
            <div>
                sidebar
            </div>
        </div>
        <div>
            footer
        </div>
    </body>
</html>
```

However, the devil's in the detail. It is semantic HTML, by default it does not apply any styles on our elements, however they are more descriptive by design and are used extensively by search enginesn and accessibility software like screen readers.

> A useful resource on what section to use and when: [HTML5 element flowchart](http://html5doctor.com/downloads/h5d-sectioning-flowchart.pdf)

