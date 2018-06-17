---
image: domain.jpg
title: "How to Use a Custom Domain On GitHub Pages"
---

GitHub Pages is a service by GitHub that provides anyone with free Web hosting for static sites. Every GitHub account is allowed one free site. This makes it *very* economical. The service even allows a user to have a custom domain (e.g., hikinthru.com). Once you have GitHub Pages going this is how you would implement a custom domain.

![Image alt]({{ site.baseurl }}/assets/images/domain.jpg)

Configuring GitHub Pages to point to your custom domain involves three steps, the first at GitHub in your site repository (your_username.github.io), and the next two at your domain registrar. These instructions make two assumptions, one, you already have a custom domain that you have purchased through a domain registrar (e.g., [GoDaddy](https://www.godaddy.com), [Google Domains](https://domains.google/), etc.) and two, that you already have a [GitHub account](https://github.com/) and have set up your [GitHub Pages](https://pages.github.com/). If either of these is not true just click the links to get started and come back as soon as you're ready.

### 1. CNAME File on GitHub

In the root of your site's GitHub Pages repository create a text file named simply CNAME, all caps with no extension. Type the root domain name at the top, without www., e.g., hikinthru.com. Save it.

This file is your Canonical Name Record. It is a very simple component of the Domain Name System, or DNS, that all of the content on the Internet is organized by. The CNAME record tells the Internet (really the machines that run it) that even though your site is hosted for example at [hikinthru.github.io](https://hikinthru.github.io) the *actual address* of your site is something different, in my case [hikinthru.com](hikinthru.com).

### CNAME File at Domain Registrar

At the domain registrar (following their instructions for editing your CNAME record), point the CNAME record to your_username.github.io, e.g., hikinthru.github.io.

### At the domain registrar, create two A records

At the domain registrar (following their instructions for editing your A record(s)), edit or create two A records that point your custom domain to the following IP addresses (good as of 3/23/2017):

* 192.30.252.153
* 192.30.252.154

### Confirm the changes with a DNS lookup service

Go to a provider such as www.whatsmydns.net and look up your custom domain. It should take a few minutes, but you should see GitHub's IP addresses show up.

## Complete Instructions from GitHub

If you have any problems, see the full instructions at GitHub's [Quick start: Setting up a custom domain](https://help.github.com/articles/quick-start-setting-up-a-custom-domain/) page.
