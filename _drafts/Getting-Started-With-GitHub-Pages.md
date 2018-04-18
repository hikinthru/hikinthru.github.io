
GitHub Pages is a free Web hosting service. Access to GitHub Pages is an automatic perk of having a GitHub account. GitHub is a free code repository designed ideally for open source code projects that rely on collaboration among many contributors. A code repository is simply a place where code is stored. It is where you go to look at, use or contribute to the source code for development projects. The text of the code is on their servers, the applications that the code makes, do not _run_ on their servers.  Code projects that  GitHub *Pages* are simply a feature of having a free GitHub account. You can go into your account repository and

If you have a local site, for example you created a new Jekyll blog with the instructions in my previous article, [Getting Started With A Jekyll Blog]({{ site.baseurl }}{% link _posts/2018-02-24-Getting-Started-With-A-Jekyll-Blog.md %}), this article will explain how to use VS Code to put your site on GitHub Pages.

## Install or update git to at least version 2.0

Check your version of git if it is already installed or you are not sure, this is mine before running this process:

```bash
git --version
git version 1.9.1
```

1. To install new or update to the latest version, in a Linux, Unix or Mac terminal add the Software Source for the Ubuntu Git Maintainers Team:

```bash
sudo add-apt-repository ppa:git-core/ppa
```

1. Update your source list:

```bash
sudo apt-get update
```

1. This command will install or if already installed, upgrade git:

```bash
sudo apt-get install git
```

After running this process:

```bash
git --version
git version 2.11.0
```

## If You Have a local copy to push up

If you have a local copy of your site that you have developed and nothing on GitHub Pages (no your_account_name.github.io site):

- Log into your GitHub account
- Go to your repository link for your_account_name.github.io if it exists and is empty, or...
- Create a new repository...