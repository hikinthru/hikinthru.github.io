

## A completely basic Jekyll blog
This involves two separate steps. First is to set up Jekyll and your site locally and make sure it is running. Second is to upload it to GitHub pages for publication.

### Method 1 with Jekyll installed, the default method from the Jekyll Website, note that this method, beginning with Jekyll 3.2, installs _layouts, _includes, and _sass in the theme-gem and not in the blog directory

1. `cd` to root directory where you want to keep the local copy of the blog
1. `jekyll new my-blog-name` e.g., slfuqua.github.io
1. `jekyll serve --watch` or
1. `bundle exec jekyll serve --watch` or
1. `jekyll build --watch`
1. In Chrome go to 'localhost:4000'

### Method 2, best method to get the full minima theme in one directory

For full instructions see GitHub [here](https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/). 

1. Go to https://github.com/jekyll/minima and download the zip file of the theme minima (or whatever base/template you wish to use for your site)
1. Unzip/extract the files into a folder with the name you will use for your repository, e.g., nynelyves.github.io. Note that the downloaded minima does not have Jekyll's default Gemfile.
1. If this is your first Jekyll site build on your local machine, issue the command: `gem install jekyll bundler`.
1. Start the jekyll server with `bundle exec jekyll serve` or `jekyll serve`. The difference is that bundler manages Ruby gem dependencies, reduces Jekyll build errors, and can help avoid environment-related bugs. If running just `jekyll serve` causes no problems you can forgo the longer command to start jekyll.
1. In your Web browser go to 'localhost:4000' to view the site.

### 

### To place your site up on Github Pages

1. Delete (if it exists) and re-create master nynelyves.github.io repository without a README, .gitignore or license file.
1. `git init` in local nynelyves.github.io
1. `git remote add origin https://github.com/nynelyves/nynelyves.github.io.git`
1. `git add .`
1. `git commit -am 'first push`
1. `git push -u origin master`

### Saw this in another tutorial on GitHub

1. In Gemfile:
1. Comment the line containing: gem "jekyll", "3.4.3"
1. Uncomment the line containing: gem "github-pages", group: :jekyll_plugins

### First push to github

1. Delete and re-create master slfuqua.github.io repository without a README
1. `git init` in local slfuqua.github.io
1. `git remote add origin https://github.com/nynelyves/nynelyves.github.io.git`
1. `git add .`
1. `git commit -am 'first push`
1. `git push -u origin master`
