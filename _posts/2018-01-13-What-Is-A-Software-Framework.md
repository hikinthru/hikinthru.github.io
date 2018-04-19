---
image: framework.jpg
title: "What Is A Software Framework?"
---

In beginning to study Web Development the term *framework* is very common, but what does it actually mean? A quick Google search on the term *framework* returns:

> a basic structure underlying a system, concept, or text.

![Image alt]({{ site.baseurl }}/assets/images/framework.jpg)

My first experience with the concept of a software framework was Bootstrap. I learned that Bootstrap had a great approach to laying out pages and getting components within them to line up nicely vertically (mostly) and horizontally, without using HTML tables. It also had other perks pre-built like jumbotrons for headers and navigation banners that were mobile responsive (collapsible on reducing the screen size), pretty easy to implement and looked great. But I still had no idea what a "framework" actually was.

I began listening to podcasts early on in my studies, such as [JavaScript Jabber](https://devchat.tv/js-jabber), [Code Newbie](http://www.codenewbie.org/) and [Shop Talk Show](http://shoptalkshow.com/) (by the way, the second two are amazing resources for new developers), and heard more and more about different "frameworks," and how some top level developers simply created their own. But created what?

Well it turns out it isn't very academic. Frameworks are simply bases for something else. That sounds obvious from the actual definition of the word, but with regard to software development I had begun to think they must be something special, even magical. That isn't true.

Microsoft Word is a framework, it abstracts all of the inner functions required to create a professional document and allows a user to type a memo or a letter without programming how to make something bold, insert the date, or change the font size of a section of text. That abstraction (a term even more commonly used in software development than "framework") makes the underlying work invisible to the user who just wants the top level functionality--quickly writing a memo. That is the key to a framework.

If you are a programmer, Web Development frameworks are akin to libraries. For non-programmers, Web Development frameworks are groups of code, written by others, typically peer-reviewed and often open-source, to accomplish common tasks. With regard to Web Development, frameworks may be presentational (the visual side, or front-end of a Web site) like Bootstrap's CSS elements, or they may be more back-end, like Jekyll's page templating tools available on GitHub.

The most significant thing about successful frameworks is that they provide a base from which an individual can build something of their own.

An example is Jekyll. Jekyll is a blogging framework that provides a scaffold for creating non-database driven blogs or Web sites. For blogs it includes the code that allows an author to easily create a page providing a list of articles with links that the author has written. The author can simply write articles in markdown (an easy to learn tagging format that can html-ize text written in a text editor), save the articles in a folder named _posts with a .markdown or .md extension, and voila, have a blog site.

Frameworks aren't magical. They are tools that allow us to skip building something from the ground up. Many experts in domains such as CSS/HTML argue vigorously that developers should skip pre-made frameworks and do their own development. This is arguable for someone who wishes to be a fully rounded developer, but not in every case. Programmers do not re-create the Math library to use Pi simply to show that they can. They import Math. Frameworks provide invaluable tools to focus on your goal, a memo, a blog, a simple Web site. Go forth and use them.