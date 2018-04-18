---
image: domain.jpg
---

Configuring your domain name to point to GitHub Pages involves three steps, the first at GitHub in the blog repository (your_username.github.io), and the next two at your domain registrar. These are the steps with GoDaddy as the registrar.

## In the github.io repository, edit or create the CNAME file in the root

Add the root domain name, without www., e.g., hikinthru.com.

## At the domain registrar, change the CNAME record

At the domain registrar (following their instructions for editing your CNAME record), point the CNAME record to your_username.github.io, e.g., hikinthru.github.io.

## At the domain registrar, create two A records

At the domain registrar (following their instructions for editing your A record(s)), edit or create two A records that point your custom domain to the following IP addresses (good as of 3/23/2017):

* 192.30.252.153
* 192.30.252.154

## Confirm the changes with a DNS lookup service

Go to a provider such as www.whatsmydns.net and look up your custom domain. It should take a few minutes, but you should see GitHub's IP addresses show up.

## Complete Instructions from GitHub

If you have any problems, see the full instructions at GitHub's [Quick start: Setting up a custom domain](https://help.github.com/articles/quick-start-setting-up-a-custom-domain/) page.
