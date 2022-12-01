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

## 1.4
