---
image: dom.jpg
title: Understanding the HTML DOM
---

The HTML DOM is the lense through which our code to create a Web page is viewed by the Web browser. Understanding the HTML DOM is critical for using JavaScript to make dynamic Web pages. Potential employers often ask Front-End applicants to explain how well they understand the DOM because everything JavaScript does to a Web page is accomplished by interfacing with it. This article explains the connection.

![Viewing code through seeing glasses]({{ site.baseurl }}/assets/images/dom.jpg)

- [Before the DOM: A Short Introduction to the Web](#before-the-dom-a-short-introduction-to-the-web)
    - [The Internet](#the-internet)
    - [HTML Documents and Hyperlinks](#html-documents-and-hyperlinks)
    - [Web Browsers](#web-browsers)
    - [Enter JavaScript](#enter-javascript)
- [Why a DOM](#why-a-dom)
    - [Application Programming Interfaces](#application-programming-interfaces)
    - [How the DOM Works](#how-the-dom-works)
    - [The DOM Standard and the W3C](#the-dom-standard-and-the-w3c)
- [Examples of Accessing the DOM](#examples-of-accessing-the-dom)
    - [Responding to a Button Click](#responding-to-a-button-click)
    - [Responding to MouseOver Events](#responding-to-mouseover-events)
- [Conclusion](#conclusion)
- [Resources](#resources)

## Before the DOM: A Short Introduction to the Web
The World Wide Web as we know it was invented and implemented in the late nineteen-eighties and early nineties by [Tim Berners-Lee](https://www.w3.org/People/Berners-Lee/). It would be a new and unique type of communication over the still nascent Internet, which preceded the Web by about twenty years.

### The Internet
The Internet is simply a group of computers with connections to each other. The beginning of the Internet in the late nineteen-sixties and early seventies had connections between a small number of research and University sites. The original two in 1968 doubled to four in 1969, and then began to quickly grow (see [The Internet Society's 'Brief History of the Internet'](#the-internet-society) under [Resources](#resources)).

![An image of the early ARPANET](http://sherriefuqua.com/pages/articles/dom/images/arpanet-original.jpg)

*A 1969 Map of* *the Entire Internet*

These connections used dedicated communication lines between special computers (early routers) at each site to transfer, direct and process the communication. The early projects were funded by the US government. Because of the immense convenience for research collaboration these connections, known then as the ARPANET (Advanced Research Projects Agency Network), began to grow in demand. 

In 1971 File Transfer Protocol, or FTP, was introduced for sharing documents via download, such as the [RFCs](https://www.ietf.org/rfc.html) (Request for Comments) that defined the growing ARPANET and today the Internet. In 1972 ARPANET was presented to the public, and in the same year email was introduced to further facilitate collaboration for researchers. Email became the primary use of the 'net' for more than a decade, but existed along with FTP, application sharing, remote access to powerful computers for researchers and students, and a growing community of Usenet users over the burgeoning network.

### HTML Documents and Hyperlinks
In the eighties Tim Berners-Lee, inside a closed network at CERN, greatly augmented earlier work and developed what we know today as the World Wide Web. He wrote the software for the first *Web server* that would allow a user to post a document for others on the network to be read by others using a document *browser* that he also developed. This was a great leap from using a networked terminal to log into a remote FTP server, download a document, and then open it with your own text editor.

These documents had to be written with a simple markup language that Berners-Lee named *HTML*, for Hypertext Markup Language. HTML simply adds tags to a document to identify page parts such as paragraphs, headings, lists, etc., and includes meta information at the beginning to describe the document for the Web browser reading it.

Below is the code for a basic HTML Web page that includes a heading, two paragraphs and a link, meta information for the browser in the header section, and a modern stylesheet to add a small amount of styling such as fonts and border spaces (note that HTML5 compliant headers require some additional information):

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>A Simple Web Page</title>
    <link rel="stylesheet" href="css/styles.css">
</head>
<body>
    <h1>A Basic HTML Web Page Heading</h1>
    <p>This is a basic paragraph.</p>
    <p>This is an HTML link to <a href="https://www.w3.org/">the W3C</a>.</p>
</body>
</html>
```

To view the page click [here](http://sherriefuqua.com/pages/articles/dom/simple.html).

What really made this new way of sharing documents revolutionary was the *hyperlinks* it introduced that could take a reader immediately from one document to another. Today links are such a paradigm for the Internet that without some thought we can't even imagine how it would work without them. But at the time it meant that any person with access to a 'connected' computer running Berners-Lee's server software, could post their document, and anyone else with the browser software and a link to it could read it. With a little work from Berners-Lee, in a short time this new way of sharing documents flowed over to the larger Internet.

Early documents on the Web were completely static pages that could only be read, with links to access other resources. There weren't even search engines, one had to know the link to a document to access it. While this was extremely useful for sharing research and government papers, it was far short of what we know today as THE Web, but it would grow.

![An image of the 1999 Internet](http://sherriefuqua.com/pages/articles/dom/images/internet-1999.gif)

*A computer generated map of the Internet in 1999 by [Bill Cheswick](http://cheswick.com/ches/map/), et. al., at Bell Labs that mapped then current trace routes across connected Internet nodes.*

### Web Browsers
In 1993, just three years after Berners-Lee publicly introduced the first basic browser and server software for hosting and accessing HTML documents, the first broadly used *graphical* Web browser, Mosaic, was released. Mosaic brought multimedia--images, sounds and video--to the emerging number of regular users accessing the Web. Mosaic soon beget Netscape, released in 1994, and the Web began to grow in content and public access exponentially.

Netscape branched from Mosaic to take advantage of the then popular and growing Java applets providing animation in Web pages. But as use of the World Wide Web grew in the mid-nineties, the Netscape team recognized the need for a more interactive and engaging experience for users. They envisioned a programming language that would allow Web pages to be manipulated on demand. This new tool would be able to react to events anywhere in the Web page (like clicks from a growingly common mouse, with Microsoft’s release of the graphical Windows 3.1 in 1992), and then through the browser respond with changes to the actual content of the Web page.

### Enter JavaScript
Early JavaScript, initially created by Netscape, was invented to fill this void. It was designed as a means to allow browsers to make changes to the HTML that defined the Web page, based on user actions (such as allowing users to 'flip' through a series of images on the page). JavaScript brought the ability to make things change with 'click' and 'rollover' mouse events or tabbing through and selecting objects, make custom information requests to the Web server on behalf of the user, push out page updates from the page provider (like news tickers), and submit forms of information back to Web sites.

Today's JavaScript is actually known as ECMASript, see [JavaScript - Resources](#javascript-resources) under [Resources](#resources) for more connections about JavaScript and ECMAScript.

## Why a DOM
The Web browser displays the Web page. This seems obvious, but it is actually very important to note the function that the browser plays as the container for the Web page. In order for JavaScript to do any incredible things to a page for the user it must have a *means* to communicate with the browser. Each browser could provide its own interface (and in the early days of JavaScript, did), but then every developer would have to write versions of every page they create for every browser it could be compatible with. The solution for this was a common standard called the DOM or **Document Object Model**.

The DOM lives in the Web browser and provides access to all of the elements within a Web page's HTML. The DOM is a part of the browser that provides a bridge, or connection, for the JavaScript code to access the Web page's HTML.

One key to its success at this is that while it is now built in to every browser such as Chrome, Internet Explorer, Firefox, Safari, etc., for the most part today these vendors do not implement their own versions of it. The DOM, as noted below, is defined by the World Wide Web Consortium (W3C) and every browser includes it, at least mostly, as the W3C defines it. There are still a few gaps that developers must work around (most notably for versions of Internet Explorer), and you will still find some minor styling/display differences in the same page displayed between Chrome and Firefox, which is why developers test in all common browsers, but for the most part vendors implement the DOM in their browsers as it is defined by the W3C.

### Application Programming Interfaces
The DOM manages a page by providing an Application Programming Interface, or API, for the JavaScript code (or other language) to connect to. An API is the 'public' side of any program. It is the DOM's API that JavaScript can access to modify the page. An API acts like a gate to a castle with a sentry at it. Like a computer port, it allows appropriate requests to pass through to the program to be processed, such as page updates or requests for information.

The DOM API provides access to the public methods (bits of code that implement changes) that the DOM defines and provides in order to manipulate each element in the page. Each element/node, depending on what it is, has certain things that can be done to it, such as changing the text content of a paragraph (known by JavaScript as `innerHTML`), or performing some function when a button is clicked 

### How the DOM Works
The DOM defines the nodes within a web page. Note that throughout this article and generally with regard to the DOM, the terms node, element, document objects, node objects, or just objects are interchangeable. The Web browser reads and processes every page it loads and everything in an HTML Web page becomes either a node object/element or a part of one, with access through the DOM.

Through the DOM JavaScript can change paragraphs, headings, comments, images, lists, footers, divs, spans, meta tags, links, or anything else that can be an element within an HTML document.

An example is a weather app that allows the user to enter a zip code to retrieve the weather. A JavaScript script sees that a zip code has been entered in a field on the page and places a request to the weather source, say [OpenWeatherMap](https://openweathermap.org), to retrieve the weather for that location. The JavaScript code must then access the HTML on the page in order to change it and display the weather for the user, change a paragraph text to display the forecast, change an icon to be a cloud or the sun, display the temperature, etc. This access to these different elements is what the DOM provides.

The DOM is ephemeral and is created as a page loads and the browser reads the HTML in it. Part of a browser’s job is to read the Web page source and create the DOM for it as the user is consuming it. The DOM then builds the page for the browser, from the original HTML, for the browser to display, and sets the parameters for everything that can happen on the page going forward, until the page is closed.

Note that the DOM however does not define HTML. HTML is a separate standard (that happens to also be defined by the W3C) that the DOM completely understands and provides a connection to. The DOM takes every HTML element when the page is read by the browser and provides the programming interface for it. This may seem a little confusing, but if a developer wishes to use a programming language, like JavaScript, to make changes to a Web page, the DOM is simply a bridge to access and modify that page's HTML.

### The DOM Standard and the W3C
The [DOM standard](https://www.w3.org/TR/dom/) is now maintained by the [W3C](https://www.w3.org), or World Wide Web Consortium, and like [HTML](https://www.w3.org/html/) is a public standard so other programming languages, not just JavaScript, can access it; however JavaScript is still the primary language used by developers to manipulate Web content in pages because it is specifically designed for this.

## Examples of Accessing the DOM
These are examples with HTML on how simply JavaScript can access the HTML of a page and make changes.

### Responding to a Button Click
This example uses a JavaScript script and the HTML DOM to assign an "onclick" event to a button element.

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>Click Me</title>
    <link rel="stylesheet" href="css/styles.css">
</head>

<body>

    <!-- An introductory paragraph -->
    <p>This example uses the HTML DOM to assign an
       'onclick' event to a button element.</p>

    <!-- A simple HTML button with an ID attribute  -->
    <button id='my_button' class='btn'>Click me</button>

    <!-- The JavaScript with an 'onclick' event -->
    <script>
    document.getElementById('my_button').onclick =
        function() {myFunction()};

    function myFunction() {
        document.getElementById('my_button').innerHTML =
        'YOU CLICKED ME!';
    }
    </script>

    <p style='padding-top: 3px;'>Refresh the page to run this again!</p>

</body>
</html>
```

To view the page click [here](http://sherriefuqua.com/pages/articles/dom/click-me.html).

This is a complete Web page (although for brevity not completely HTML5 compliant) that displays a simple paragraph, a button, and another paragraph; note that everything inside the `<script>` element is invisible to the user viewing the page. This is an explanation of the page:

* The button is created with the HTML `button` element. It is given an `id` that JavaScript will use to access it.
* The script includes two blocks of code, the first begins with `document`, this is the root-node of and top object in the DOM tree of the page.
* `.getElementById` is a method that the DOM provides to manipulate any elements that include a defined id in the page, like the button element above.
The script then provides the id to be affected: `my_button`.
* `.onclick` is the event that triggers whatever instructions follow.
* `myFunction` is called to respond to the click event.
* In the second section of the script `document.getElementById('my_button')` all mean the same as the first section.
* `.innerHTML` is a property of all text elements such as paragraphs (or headings, labels, etc.), and refers to the text wrapped inside the element (e.g., `<p>Any text</p>`).
* The assignment operator `=` then reassigns the text property of the button to ‘YOU CLICKED ME!’.

All attributes of elements can be changed with JavaScript through the DOM: styles (appearance), content, behaviors (like animations), etc.

Events can be triggered by many things such as key presses, button clicks, hovering over an element (like a tooltip that pops up when your mouse moves over a word or section of a page), the page originally loading, or re-loading (requiring no interaction from the user), and much more.

### Responding to MouseOver Events
Another example, this time using mouseover, or *hover* events:

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <title>Mouse Events</title>
    <link rel="stylesheet" href="css/styles.css">
</head>

<body>

    <!-- An introductory paragraph -->
    <p>Using a Script to React to Mouse Events:</p>

    <!-- Calling the script functions based on mouse events:
    'onmouseover' and 'onmouseout' -->
    <!-- Note that the 'class' is just for styling -->
    <div class='mouse-over'
         onmouseover='mOver(this)'
         onmouseout='mOut(this)'>

    <!-- The initial button text -->
    This is a magical orange box

    <!-- The JavaScript with 'mouseover' and 'mouseout' responses-->
    <script>
    function mOver(obj) {
        obj.innerHTML = 'Thanks for moving your mouse over me!'
    }
    function mOut(obj) {
        obj.innerHTML = 'You left me! Please come back!'
    }
    </script>
    </div>

</body>

</html>
```

To view the page click [here](http://sherriefuqua.com/pages/articles/dom/mouse-over.html).

This is an explanation of the page:

* The important section begins with an HTML `<div>`, an invisible element that makes a container for other elements, in this case the orange box on the page.
* The `<div>` informs the DOM that on two events, `onmouseover` and `onmouseout`, execute the JavaScript functions `mOver` and `mOut`, defined by the programmer.
* The `<div>` contains the text 'Move your mouse over me!', this is the original text in the box.
* The script section, still within the `<div>`, contains the two functions that define what to do when they are activated, or 'called'.
* Entering the box with your cursor triggers `onmouseover` through the DOM, which calls `mOver` from the script. `mOver` then changes the text, or `innerHTML` in the box, to 'Thanks for moving your mouse over me!'.
* Moving out of the box with your cursor triggers `onmouseout` through the DOM, which calls `mOut` from the script. `mOut` then changes the text, or `innerHTML` in the box, to 'You left me!'.

This is an example of the common practice of modifying elements on a page when the mouse moves across them. For instance most people are familiar with a button changing (getting a glow or getting a bit larger, etc.) when your mouse passes over it to indicate that it is actionable.

---

These examples show just a couple of approaches JavaScript can use to access the DOM and change the content of a page. JavaScript is a programming language with wide capabilities today, but it is at its best when creating 'magic' on Web pages.

## Conclusion
That is a brief introduction to what the DOM does and is for, and why understanding it is an integral part of Web Development and learning JavaScript. There is a list of links below with much more information about the DOM, HTML and JavaScript.

## Resources

#### The Internet Society
https://www.internetsociety.org/internet/what-internet/history-internet/brief-history-internet

#### The W3C HTML DOM Standard
https://www.w3.org/DOM/

#### The HTML Standard
https://www.w3.org/html/

#### History of the Web Browser
https://en.wikipedia.org/wiki/History_of_the_web_browser

#### JavaScript - Technical
https://developer.mozilla.org/en-US/docs/Web/JavaScript

#### JavaScript - General
https://en.wikipedia.org/wiki/JavaScript

#### JavaScript - Resources
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Language_Resources
