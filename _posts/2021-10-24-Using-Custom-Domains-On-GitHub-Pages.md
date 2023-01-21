---
image: domain.jpg
title: "Using a Custom Domain On GitHub Pages"
---

GitHub Pages is a service by GitHub that provides free Web hosting to anyone for a static Website (no PHP, mySQL, etc.). Every GitHub account is allowed one free site. This makes it *very* economical for individuals wanting to dabble in Web development without paying for hosting, to dabble away. The service also allows a user to have a custom domain if they want to (e.g., hikinthru.com). And 'static site' doesn't mean it doesn't 'do' anything. I use Jekyll on my site so that all I have to do is upload my new post and the site does all the work. I'll write more on that later, but you can see what you can do with a static site on Jekyll's pages [here](https://jekyllrb.com/). 

![Image alt]({{ site.baseurl }}/assets/images/domain.jpg)

For a [Quickstart](https://docs.github.com/en/pages/quickstart) on using GitHub Pages' free Website check out the link. It also has more links to in depth information about various features and paid options. But GitHub will host a completely free, public (anyone can look at the code and files) site, with up to 500 MB of storage--as of this update in January, 2023.

Once you have GitHub Pages going on your free account, these instructions explain how you can implement a custom domain.

Know that buying a domain alone is much cheaper than both paying for a domain and the hosting for your pages on that domain, because nothing says you must buy them together. You can usually get a good deal on both for the first year, but then you have to pay full price. I paid GoDaddy \$19.19 for hikinthru.com, just the name, no hosting, last March for the year. I've had it over ten years and it goes up a few cents a year. Keep in mind that different domains (e.g., .io, .com, .net, etc.) cost different amounts, depending on how in demand they are.

It's just three steps to configure GitHub Pages to reflect your custom domain. The first at is GitHub in your Website repository. Before your custom domain is set up, this site is accessed on the Internet at the address your_username.github.io. And the next two are at your domain registrar, the people you paid for your domain.

These instructions make three assumptions, one, you already have a custom domain that you have purchased through a domain registrar (e.g., [GoDaddy](https://www.godaddy.com), [Google Domains](https://domains.google/), etc.), two, that you already have a [GitHub account](https://github.com/), and *three*, that you have set up and tested your [GitHub Pages](https://pages.github.com/) at your_username.github.io. If any of these is not true just click the links to get started and come back as soon as you're ready.

### The First Step is the CNAME Record at GitHub

In the root of your site's GitHub Pages repository create a text file named simply CNAME, all caps with no extension. Type the root domain name at the top, without www., e.g., just 'hikinthru.com'. Save the file and close it, you are done with it.

This file is your Canonical Name Record. It is a very simple component of the Domain Name System, or DNS, that all of the content on the Internet is organized by. The CNAME record tells the Internet (really the machines that run it) that even though your site is hosted for example at [hikinthru.github.io](https://hikinthru.github.io), the *actual address* of your site that anyone would type into a Web browser to get to, is something different, in my case [hikinthru.com](hikinthru.com).

### The Second Step is the CNAME Record at Your Domain Registrar

At the domain registrar search for and follow the instructions for editing your CNAME record on *their* site. You will follow the instructions (they all provide them and they can all be different), and point the CNAME record to 'your_username.github.io', e.g., hikinthru.github.io. Now the two CNAME records, one where your files are, and the one at the registrar, are pointing at each other.

An aside about what your registrar actually does. When you purchase a domain, you are paying that registrar or reseller (there's a difference, but beyond the scope of this brief explanation), in my case GoDaddy, to hold on to the records for your domain, including your CNAME file and A records, which we'll discuss next. The registrar keeps those records, which are part of the domain name system, or DNS, on servers that can be read by the DNS servers that make up the backbone of the Internet. This is why where you pay for your domain, and where you host the files for your site, are completely separate things. Hosting services are the real income for the registrars and domain resellers for being in the business of selling domain names. The domain names themselves are internationally allocated by ICANN, the non-profit Internet Corporation for Assigned Names and Numbers.

### The Third Step is the A Records at the Domain Registrar

At the domain registrar (following their instructions for editing your A record(s)), you will edit or create, two A records that point your custom domain to the following GitHub server IP addresses (still working as of this update in January, 2023, and at any time forward, if you are reading this they are still working):

* 192.30.252.153
* 192.30.252.154

This tells the domain name system what physical machines to go to, to get to your Website files. The system requires two server addresses for redundancy in case one of them is down.

### Confirm the Changes with a DNS lookup Service

Go to a provider such as www.whatsmydns.net and look up your custom domain. It should take a few minutes to show up, but you should see GitHub's IP addresses after a bit.

## Dig Deeper into GitHub Pages and What They Can Offer at GitHub

You can find more information and links at [GitHub's site](https://help.github.com/articles/quick-start-setting-up-a-custom-domain/) on custom domains with GitHub Pages, as well as all of the other services available.
