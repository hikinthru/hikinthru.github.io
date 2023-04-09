
#### First things

We're going to discuss getting an already existent Jekyll site to run on a local server. This article includes instructions for a Mac running MAMP on macOS 13, Ventura. Most of these instructions will apply to a Linux machine with LAMP, and the outline of the instructions will apply to Windows. 

For help on how to build a Jekyll site, you can find the instructions at Jekyll's Web site [here](https://jekyllrb.com/docs/).

The totality of these instructions come from all over the Web. Some of the sections will be taken directly from Web sites, along with references to where they are from. The point is to put it all together in one place, for your use and my future reference.

#### Starting with Jekyll

1. Install all prerequisites: 
   - Ruby version 2.5 or highter
   - RubyGems
   - GCC
   - Make
  
If you do not know if you have all of these installed, or are not sure, go to [Jekyll's Requirements page](https://jekyllrb.com/docs/installation/#requirements) to check. It includes instructions if you need add or upgrade anything.

2. Follow the instructions [here](https://gist.github.com/MichaelCurrin/61053a564bdb3098bae11f949bab3578) (repeated below) to set up Jekyll. DO NOT just go and install Jekyll and Ruby (or vise-a-versa) on a Mac because Apple has a version of Ruby installed that has special privileges and we don't want to change those files. 
   
   1. Install development tools if they are not already:
   
    ```zsh
    xcode-select --install
    ```

    2. Install Ruby v.2.7 with Homebrew. If you do not have Homebrew installed on your Mac, you should, you will need it for Webdev. The installation files are [here](https://brew.sh/). We're not installing v.3.x yet do to a bug with Ruby and Jekyll, which isn't fixed as of this post on 1/23/2023. When it is installed, come back. Now issue this command to install Ruby:

    ```zsh
    brew install ruby@2.7
    ```

    3. Edit the configuration file for the shell you are using. For zsh you will edit '~/.zshrc` or `~/.zshenv`. Add the following to the config file, ensuring that our installation of Ruby does not interfere with Apple's:

    ```zsh
    RUBY_HOME=/usr/local/opt/ruby/bin
    export PATH="$RUBY_HOME:$PATH"
    ```

   3. Install jellyll and bundler:

    ```zsh
    gem install jekyll bundler --user-install
    ```






3. Open **Bash on Ubuntu on Windows** or **Git Bash**
4. Change to the directory you wish to serve
   cd '/mnt/c/Users/sherrie/Dropbox/blogs/hikinthru.github.io'
5. Execute:
   `bundle exec jekyll serve`
   If you get the error:
6. `Could not locate Gemfile or .bundle/ directory`
   Go back to step 2.
