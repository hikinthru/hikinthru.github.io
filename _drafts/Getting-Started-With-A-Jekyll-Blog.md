
Jekyll is an wonderful tool for making a simple Website or blog. It removes the need to repeat code on each page for things like navigation or headers and footers. By design it is especially useful for blogs. Here you will learn what Jekyll is, how it works, how to install it on your computer, and step through how to begin a simple blog that requires little maintenance but the addition of posts.

- [What Jekyll Is](#what-jekyll-is)
- [How Jekyll Works - Ruby Gems](#how-jekyll-works---ruby-gems)
- [What These Instructions Will Accomplish](#what-these-instructions-will-accomplish)
- [Requisites](#requisites)
- [Installing Jekyll On Your Computer](#installing-jekyll-on-your-computer)
  - [For GitHub Pages Users](#for-github-pages-users)
- [File Structure](#file-structure)
- [Customizing Our Blog - The `_config.yml` File](#customizing-our-blog---the-configyml-file)
- [Customizing Our Blog - The `about.md` File](#customizing-our-blog---the-aboutmd-file)
- [Adding New Posts](#adding-new-posts)
- [Jekyll Themes](#jekyll-themes)
- [Jekyll Commands Quick Reference](#jekyll-commands-quick-reference)
- [Further Reading](#further-reading)

## What Jekyll Is

Jekyll is a Web templating system. A template system is used on the Web to more efficiently maintain Web sites by separating content (for example the blog articles that you write, or the text in an "About" or "Events" page on a site) from the programming of the entire Web site that the page is posted on. These systems are also called CMSs, or Content Management Systems. CMSs have a great range of complexity and a templating system like Jekyll is a simpler version of a CMS that can display and format the navigation links, the footers, the columns--essentially any of the information that is re-used for the pages throughout the site--around commonly updated content.

Jekyll is a program that takes the separate pieces of the site that you create, the navigation links, footer, header, blog posts, the text content of your landing and about pages, etc., all existing in text files, and "builds" them into the page(s) that you see in a Web browser when you view the site. It goes a little further with blog entries and is sometimes described as "blog-aware," because it can take properly formatted and named blog articles and organize and list them automatically. Therefore adding a blog post is as simple as putting your post file in the right place with the right name. This is discussed further below under [Adding New Posts](#adding-new-posts).

Jekyll is used to build "static" Web sites. A static site is not as boring as it sounds, the term means that the site does not use a database to generate its pages such as, for example WordPress. Jekyll is much less complex and uses text files to form and manipulate the site. There is still a small learning curve for Jekyll but it is far lower than mastering Word Press to create the site you envision.

### Gems And Plugins - Clarifying Terms

In starting to work with Jekyll you will encounter the term _gems_ often, we'll cover them briefly. As mentioned, the Jekyll program is written in Ruby. Ruby is a programming language often used to build Web applications like Jekyll or almost entirely program sites like GitHub. When a program written in Ruby is packaged (bundled up to be distributed for people to use, like an .exe file for Windows) the Ruby software package is called a __gem__. Ruby gems are typically applications like Jekyll that do something useful or they are software libraries (a re-usable group of code) that provide additional programming options for Ruby programmers.

Ruby, like Python, is a scripted language. This means that its program files are simply human readable text files that are specially processed by the operating system when they are used. Ruby gems are text files that include the code that provides the gem's functionality, documentation about how it functions and meta data describing at minimum what files are included, test information, computer platforms it will run on, its version number, and the author's name and contact information.

I want to briefly touch on the term __plugin__. Jekyll is a Ruby gem, but is also called a Ruby __plugin__ because it relies on a Ruby environment (which exists on almost all Web servers). Jekyll additionally has its own plugins. A plugin is simply a piece of software, in any language, that relies on something already in the environment to run.

## What These Instructions Will Accomplish

After following these instructions you will have a running version of Jekyll (including its Web server) on your computer. You will have a local (that is, on your computer) blog Web site that you can view in your browser. Your blog will have the default Jekyll theme named **minima**.

If you wish, after following these instructions you can take the next step and upload your new blog to a [GitHub Pages](https://pages.github.com/) account for free, or any other Web host that supports Jekyll (almost all). For more information on providers other than GitHub see the Deployment methods page at [jekyllrb.com](https://jekyllrb.com/docs/deployment-methods/). For the next step of putting your Jekyll site on GitHub Pages see my article [Getting Started With GitHub Pages]({{ site.baseurl }}{% link _posts/2018-02-25-Getting-Started-With-GitHub-Pages.md %}).

## Requisites

If you are missing any of these necessary components there are many great articles online for installing and setting them up.

- The operating system: GNU/Linux, Unix, MacOS, or Windows 10 - Anniversary Update version, with Bash running on the Windows Subsystem for Linux (Bash on Ubuntu on Windows is the most common installation for this)
- Ruby version 2.2.5 or above with development headers (`ruby -v`, development headers can be checked on Ubuntu/Bash by running `apt list --installed  ruby-dev`)
- RubyGems (`gem -v`)
- GCC and Make (`gcc -v`, `g++ -v`, `make -v`)
- Jekyll (`jekyll --version` or `gem install jekyll`)

## Installing Jekyll On Your Computer

You will issue the commands below from a terminal (e.g., Bash). Jekyll and Bundler are plugins for Ruby and are called Ruby gems (we discussed this about Jekyll earlier). **RubyGems** (no space, 'R' and 'G' capped) conversely, is the _package management system_ for Ruby (like `rpm` for Node or `apt-get` for Debian/Ubuntu systems) and is invoked with the command `gem`.

Replace `site_name` in each command below with a name for your site. It can be your user name on GitHub, the full site url, or any name with no spaces or slashes to identify your site.

You may need to prefix the first two instructions below with `sudo` or a similar admin command for your system.

```bash
# Install Jekyll and Bundler gems through RubyGems
gem install jekyll bundler

# Create a new Jekyll site at ./site_name
jekyll new site_name

# Change into your new directory
cd site_name

# Build the site on the preview server (this system)
bundle exec jekyll serve

# The last two lines should read...
    Server address: http://127.0.0.1:4000/
  Server running... press ctrl-c to stop.
```

Now open your browser of choice and go to [http://localhost:4000](http://localhost:4000).

### For GitHub Pages Users

A few additional steps are required if you plan to host your site on GitHub pages and synchronize it between GitHub and your computer. GitHub Pages requires its own Ruby gem installed in your local environment, intuitively called the _GitHub Pages Gem_.

- In your new site folder edit the file `Gemfile` with the following changes:

```bash
# Comment this line if it exists by placing a hash/pound sign at the
# beginning:
# gem "jekyll", "~> 3.7.2"

# Add this line or if it already exists uncomment it (remove the
# hash/pound sign at the beginning):
gem 'github-pages', group: :jekyll_plugins
```

- Save the file.

- Stop the Jekyll server if it is running.

- In the terminal run `bundle update`.

- In the terminal run `bundle install`.

- To view everything installed for your GitHub Pages you can run `bundle exec github-pages versions`.

- Re-issue the command `bundle exec jekyll serve` to restart the server.

Connecting your new site to GitHub Pages is outside the scope of this article. If you plan to do so follow the instructions above, continue with this tutorial, and then read the article [Getting Started With GitHub Pages]({{ site.baseurl }}{% link _posts/2018-02-25-Getting-Started-With-GitHub-Pages.md %}).

## File Structure

The default file structure for the installation we just completed is:

```bash
.
├── 404.html
├── about.md
├── _config.yml
├── Gemfile
├── Gemfile.lock
├── index.md
└── _posts
    └── 2018-02-25-welcome-to-jekyll.markdown
```

Included in this folder are the files that users most commonly modify, including two that we will edit in this tutorial, `_config.yml` and `about.md`.

Additionally, in `/var/lib/gems/2.3.0/gems/minima-2.1.1` are the following component files for our site:

```bash
.
├── assets
│   └── main.scss
├── _includes
│   ├── disqus_comments.html
│   ├── footer.html
│   ├── google-analytics.html
│   ├── header.html
│   ├── head.html
│   ├── icon-github.html
│   ├── icon-github.svg
│   ├── icon-twitter.html
│   └── icon-twitter.svg
├── _layouts
│   ├── default.html
│   ├── home.html
│   ├── page.html
│   └── post.html
├── LICENSE.txt
├── README.md
└── _sass
    ├── minima
    │   ├── _base.scss
    │   ├── _layout.scss
    │   └── _syntax-highlighting.scss
    └── minima.scss
```

Since this is a relatively brief introduction to Jekyll we can't go into all of the files included in the installation. But the presentation of the site is controlled by the files in the gems folder for the theme you are using (like ours just above). Modifying this layout can be a lot of fun and much more information on doing that can be found at the official Jekyll site: [jekyllrb.com](jekyllrb.com) under Docs.

## Customizing Our Blog - The `_config.yml` File

Using a text editor (I am using VS Code by Microsoft, but if you don't feel like installing anything NotePad, Gedit, or TextEdit are perfectly sufficient) open the file `_config.yml` in your Jekyll site folder.

You will see a bunch of lines at the top that begin with `#` signs. In programming this is called a _hash_ not a pound sign. In Jekyll a line that begins with a hash is a comment. It either provides information or it is a command that has been disabled.

About halfway down the file lines begin without hash tags.

`title:` Enter a title for your site, like "Sherrie Fuqua's Technical Blog" or whatever the site's purpose will be in brief.
`email:` If you wish to post a contact method on your public page (all free repositories posted on GitHub are public) enter your email in separate discrete sections like so: nynelyves @ gmail . com. This helps prevent programmed "scrapers" from gathering your email for spamming.
`description:` Remove the `>` and additional text to add your description. For search engines, if you are going to post this online (e.g., on GitHub Pages) you should include your name and the type of content you will be covering, such as, "Sherrie Fuqua's blog for technical topics including JavaScript, Python, Web Development, Jekyll, Git, GitHub, the Internet and computers."
`baseurl:` We do not need to change this.
`url:` We do not need to change this.
`twitter_username:` Your twitter account handle if you wish to publish it, if you place a hash before `twitter_username:` to comment it out.
`github_username:`  Your GitHub account name if you wish to publish it, if you place a hash before `github_username:` to comment it out.

Below this section the `Build settings` begin and we will not make any changes there.

## Customizing Our Blog - The `about.md` File

Using your text editor, open the file `about.md` in your Jekyll site's root.

At the top of the file you see:

```bash
---
layout: page
title: About
permalink: /about/
---
```

We won't change any of this information. Everything below the bottom three dashes `---` however is ours to do whatever we wish. Include a brief bio (or a longer one if you prefer) and a description of what your site will be about. This is a markdown file, you can include text, lists, links, images, etc. GitHub has more information on [Mastering Markdown](https://guides.github.com/features/mastering-markdown/), it is truly not complex.

## Adding New Posts

In the folder on your computer where you installed your site you will find a subfolder named `_posts`. Adding a post to your blog is as simple as putting a markdown or HTML file in this folder with the filename format of `YYYY-MM-DD-name-of-post.ext` and reloading the list page of your blog. Jekyll updates the list.

Markdown is a very simple way of writing text that can be formated like the article you are reading now, using things like `#`s to indicate section titles, dashes (`-`) to indicate lists, etc. An excellent starting reference is [here](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#links).

## Jekyll Themes

Jekyll themes are used to organize, manage and define the presentation of your Jekyll site. There are many free Jekyll themes on the Internet and there are several available through GitHub Pages. We have installed the default Jekyll theme, _minima_.

## Jekyll Commands Quick Reference

```bash
# Start the Jekyll Server
bundle exec jekyll serve

# View everything installed for your GitHub Pages
bundle exec github-pages versions
```

## Further Reading

- A great source of information is the official Jekyll documentation at [https://jekyllrb.com/docs/home/](https://jekyllrb.com/docs/home/).
- Liquid is the templating language used by Jekyll to introduce variables and re-use information such as the site title or description that we set in the `_config.yml` file. See more information by Adobe [here](https://docs.worldsecuresystems.com/developers/liquid/introduction-to-liquid).
- More information on [GitHub Pages](https://pages.github.com/).