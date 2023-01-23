
## TODO

- Increase font size, make white
- There is a jump when going to "About" or "Contacts", a re-alignment of the page, fix it
- Add typewriter font, read: http://www.1001fonts.com/typewriter-fonts.html
- x Add three recents posts (only) to side bar
- Add image to top of default page
- Add images to posts
- Add post list with excerpts to default
- Add author name, description, etc. when moving to hikinthru
- Get left side to scroll
- Make default page image a url
- find 'about.md'

## Folder to be in to run Jekyll from Bash

/mnt/c/Users/sherrie/Documents/GitHub/nynelyves.github.io

## Command to start local serve

bundle exec jekyll serve

## To synchronize Git

Commit or push in VS Code, open Github Desktop and click Push to Origin in the top

## Best size for a jumbotron image

The best dimension to use is 1600 x 800, or simply an image that has a 2:1 image ratio.

## Add a font to a Jekyll site

- Add a `<link>` line to the head section.
- Check this page: http://dmcwo.com//a-post-about-pages/

## Add Bootstrap components to a Jekyll site

Instructions at https://simpleit.rocks/how-to-add-bootstrap-4-to-jekyll-the-right-way/

### Requisites (determine current versions installed, in parentheses)

- Ruby (`ruby -v`)
- Jekyll (`jekyll -v`)
- Popper (`npm install popper.js --save` intentionally exclude `sudo` at the beginning)
- jQuery (`npm install jquery --save` intentionally exclude `sudo` at the beginning)
- npm, yarn or bower package installer to install bootstrap, the instructions below are for yarn (bower is becoming deprecated, yarn installs dependencies in parallel as opposed to serially and is therefore faster, it can also install pre-downloaded applications via cache while offline.)

### Configuring our environment

- At our local Jekyll/GitHub repo root folder we install bootstrap (see below to do this with yarn)
- In the `_config.yml` file add the lines:

```text
sass:
    load_paths:
        - _sass
        - node_modules
```

This text allows Jekyll to process our Sass files.

- And:

```text
exclude: []
```

To remove all default exclusions, mainly including the folder `node_modules` where bootstrap is now installed.

## Install yarn for Wind ows and then Bootstrap 4

1. Follow the installation instructions on the website https://yarnpkg.com/lang/en/docs/install/ and add the repo
2. Ensure node.js is installed
3. Download the installer at the above link

That didn't quite work. Trying again:

1. `cd` to repository location
2. Open bash as admin, type `sudo -i` and enter password
3. `curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -`
4. `echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list`
5. `apt-get update && apt-get install yarn`
6. Yarn is now installed (apparently properly)
7. Install Bootstrap 4.0: `yarn add bootstrap@4.0`
8. If errors for jQuery and popper dependencies then,
9. `yarn add jquery` and include sudo even though elevated
10. `yarn add popper.js`
11. Re-run `yarn add bootstrap@4.0`
12. To be safe I also ran: `sudo npm install bootstrap@4.0 --save`

Note that these errors are fine:
warning package.json: No license field
warning No license field

## Calling resources on .html pages
call you resources with :

- <link rel="stylesheet" href="{{ site.baseurl }}/css/css.css">
- <script src="{{ site.baseurl }}/js/scripts.js"></script>
- <img src="{{ site.baseurl }}/path/to/img/toto.jpg">
- <a href="{{ site.baseurl }}/linkto/">Link</a>