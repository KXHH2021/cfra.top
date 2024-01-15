---
title: HTML+JS+CSS Basic-1.html
categories:
  - Study Tutorials
tags:
  - CSS
  - HTML
  - JS
description: >-
  This article serves as a dictionary for my own work and study, so readers are
  welcome to bookmark and use it. The author is a back-end development front-end
  dabbling is not deep, so the article focuses on the breadth and practicality,
  the principle and performance will not be too much in-depth.
cover: >-
  https://raw.githubusercontent.com/KXHH2021/seveimg/main/img/202310032010660.jpg
abbrlink: 20924
date: 2023-10-03 20:04:47
---

![html-css-javascript](https://raw.githubusercontent.com/KXHH2021/seveimg/main/img/202310032010660.jpg)

## 1.html

### 1.1 html5 page structure

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>title</title>
        <link rel="icon"  href="data:image/png;base64,i..." type="image/x-icon">
  <link rel="shortcut icon" href="data:image/png;base64,...=" type="image/x-icon">
    </head>
    
    <body>
    </body>
</html>

```

### 1.2 The html tags include the head tag and the body tag:

(1) The head tag can define the character encoding format, as well as the title and icon of the page.
(2) The content displayed on the page needs to be defined in the body.

### 1.3 Introducing js in html:

(1) The internal inserted code format is as follows:

```javascript
<script type="text/javascript">
 // JavaScript code
</script>

```

(2) Introducing js external files：

```javascript
<script type="text/javascript" src="file path">
```

Generally introduced at the bottom of the body tag to ensure that all DOM elements are loaded before loading the JS file.
Note that when loading multiple JS files, if there is a dependency, you need to ensure that the dependent file is introduced first. So you will first introduce the three-way library such as jquery, and then introduce the business JS file.

### 1.4 Introducing styles in html:

(1) Inline Styles：

```html
<h1 style="margin-left: 40px;">Inline Style</h1>

```

Style directly in the DOM element using the style attribute, the highest priority; not conducive to maintenance.

(2) Inline style：

```html
<head>
    <title>Inline Style</title>
    <style>
        h1 {
            margin-left: 40px;
        }
    </style>
</head>

```

Introduced in the HEAD via the style tag.

(3) External style sheets：

```html
<link rel="stylesheet" href="./css/index.css">
```

Introduced via the href of the link tag.

(4) Importing style sheets：

```html
<link rel="stylesheet" href="./css/index.css">
```

in the index.css file:

```css
@import "1.css";
@import "2.css";
@import "3.css";
@import "4.css";
```

Note: Multiple stylesheets introduced in a single html file will override the former if the selectors are duplicated.

### 1.5 Common elements: block and inline

DOM elements as a whole can be categorized into two types: block elements and inline elements. Block elements can be used for layout and inline elements can be used for display. The main differences between the two are:
(1) Block elements can contain block elements, inline elements, and text; inline elements can only contain inline elements and text;
(2) Block and other elements have line breaks; inline elements do not have line breaks;
(3) Block elements can set the height (height) and width (width), inline elements can not be set.
Common block-level elements are: div, p/h, table/form, ul/ol, hr
Common inline elements are: span, a, img, input/textarea, br

### 1.6 Dom native syntax

With the advent of jquery, DOM native statements are basically not used anymore.

```javascript
(1)Getting DOM objects
#Returns the object with the specified id
document.getElementById('id attribute value');

#Returns a collection of objects with the specified type
document.getElementsByClassName('class attribute value');

#Returns a collection of objects with the specified tag name
document.getElementsByTagName('label name');
...
```

Next articleNarrative javascript
