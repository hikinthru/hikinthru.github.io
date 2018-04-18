
## What is Jekyll
I built my first site, my personal site, mostly from scratch (I employed Bootstrap's CSS for responsiveness and the grid). It has five pages including the landing page. I wanted a primary column for content and a right column, mainly to list my blog articles.

As I learned about building a full site, I had to rearrange my files several times. Each change to my directory structure involved manually re-writing the navigation links on each page. Adding a blog article involved manually updating the right column content on every page to add the new link. Any change to the footer required manually changing every page. All of this required testing and making sure five times for each change that I made no typos.

There are other frameworks to solve this problem, but when I started using GitHub I discovered Jekyll and decided to commit to it.

## What This Article Covers
This article will cover creating a Jekyll 3 Website with a landing page, a blog, a portfolio page, an about page and a contact page. It will also cover serving these pages both locally on your computer for working on the site, and serving them on GitHub pages (github.io).

For the purposes of this article I am building a new site from scratch at [https://nynelyves.github.io/](https://nynelyves.github.io/). We will start with creating the site on our computer (our *local* copy) and then we'll put it up on GitHub.

## Jekyll Prerequisites
These instructions are for Linux and MacOS. For Windows please see Jekyll's full documentation [here](https://jekyllrb.com/docs/windows/).

The following components can be downloaded and installed at their links if you do not already have them installed.

* [Ruby](https://www.ruby-lang.org/en/downloads/) version 2.0 or above, including all development headers. You can check your version of Ruby with `ruby -v` at the command line.
* [RubyGems](https://rubygems.org/pages/download). You can check to see if you already have gems installed by issuing `gem` at the command line. If RubyGems are already installed you can make sure all your gems are up to date by issuing `gem update` at the command prompt (you'll need `sudo` on many Linux systems).
* [GCC](https://gcc.gnu.org/install/) and [Make](https://www.gnu.org/software/make/). You can check to see if you already have these by running `gcc -v` and `make -v` at the command line.
* MacOS only - install [Xcode](https://itunes.apple.com/us/app/xcode/id497799835?mt=12) and the Command-Line Tools it ships with. Xcode is an Apple developer kit. Click the link or go to Preferences -> Downloads -> Components.

## Install Jekyll Locally
Once all of the prerequisites are met for your environment, open a command line and issue:

```bash
gem install jekyll
```

That's it! If you experience any problems you can check Jekyll's [Troubleshooting pages](https://jekyllrb.com/docs/troubleshooting/) for help.

## Get a Jekyll Theme

* Create a local folder with the name of your blog/web site.
* Download a Jekyll theme. For the purposes of this article we will start with the default Jekyll theme *Minima* from [https://github.com/jekyll/minima](https://github.com/jekyll/minima).

## Start the jekyll server
Open terminal and `cd` to the folder holding the jekyll site to serve. Issue the command `jekyll serve`. That's it.

In case of an error regarding gemfile versions, try `bundle update json`, which may also suggest `sudo gem install bundler`. If that does not work start the server with `bundle exec jekyll serve`. Using `bundle exec` sorts out Ruby gemfile version and lock issues.

You may see instructions to use `jekyll serve --watch` so that the server dynamically looks for changes while it is running, note that as of jekyll 2.4 this is no longer necessary as `watch` is now the default. To disable this issue, `jekyll serve --no-watch`.

Note that `jekyll serve` automatically runs `jekyll build`. The `build` command is useful if running git from terminal for the master site where a server is already running. learning.

Note that the switch `--watch` is unnecessary after version 2.4.

## TODO

* Test responsiveness on first page

## Notes

* Page width, 180 to 920 = 740 px width for images
