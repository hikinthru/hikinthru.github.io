---
image: vs-code-git.png
---

If you are new to GitHub Pages and have not yet placed a repository there, I suggest you begin with my article on [Getting Started With A Jekyll Blog]({{ site.baseurl }}{% link _posts/2018-02-24-Getting-Started-With-A-Jekyll-Blog.md %}).

If you already have a repository on GitHub Pages, you can place a copy of your GitHub Pages on your local computer for viewing and editing so that you don't have to use GitHub's online editor, or even manually upload posts and updates with your terminal. My choice of code editors is Microsoft's Visual Studio Code. Over the years, I have used Eclipse, eMacs, Vi/Vim, Notepad++, Sublime (great editor, but I don't find it worth $79), Atom (really a free reproduction of Sublime), and finally VS Code, which is really just a port of Atom, but faster on a PC. I'm very satisfied with Code, its speed, ongoing support from the open-source community, and its wealth of extensions. It can be a RAM hog, but no more than Atom or Sublime. These are the instructions on how to set up VS Code to edit a GitHub Pages blog (or any repository) on Ubuntu Linux.

- [1. Install or update (if already installed) git to at least version 2.0](#1-install-or-update-if-already-installed-git-to-at-least-version-2-0)
- [2. Clone Your Repo to a Local Copy](#2-clone-your-repo-to-a-local-copy)
- [3. In VS Code...](#3-in-vs-code)
- [4. To Post Updates](#4-to-post-updates)
- [5. To Add New Files to Your Repo](#5-to-add-new-files-to-your-repo)

## 1. Install or update (if already installed) git to at least version 2.0

Check your version of git. This is mine before running this process:

    sherrie@dell:~$ git --version
    git version 1.9.1

1. To get the latest version, in a terminal, add the Software Source for the Ubuntu Git Maintainers Team:

        sherrie@dell:~$ sudo add-apt-repository ppa:git-core/ppa

1. Update your source list:

        sherrie@dell:~$ sudo apt-get update

1. This command will install or, if already installed, upgrade git:

        sherrie@dell:~$ sudo apt-get install git

After running this process:

    sherrie@dell:~$ git --version
    git version 2.11.0

## 2. Clone Your Repo to a Local Copy

A *repo* is a repository. It's an isolated space in your GitHub. In a terminal, `cd` to the local folder where you wish your local repo to live. In this example, my folder is named 'local'. Git will create a new folder in this space with the name of your repo. In this example, my new folder will be named 'hikinthru.github.io', and because we are using `git clone`, it will automatically be initialized as a local git repository. Issue the following command with the full URL of your repository:

    local$ git clone https://github.com/hikinthru/hikinthru.github.io

You should see the following confirmation with your information:

    Cloning into 'hikinthru.github.io'...
    remote: Counting objects: 1439, done.
    remote: Compressing objects: 100% (5/5), done.
    remote: Total 1439 (delta 1), reused 0 (delta 0), pack-reused 1433
    Receiving objects: 100% (1439/1439), 8.23 MiB | 2.20 MiB/s, done.
    Resolving deltas: 100% (794/794), done.

You will now see a copy of your GitHub repo in your local folder.

## 3. In VS Code

1. Close any open folders

1. Click File, Open Folder (Ctrl K, Ctrl O)

1. Select your local repository.

1. Click the GitHub icon in the activity bar on the left in Code. You should not see a message to 'Initialize Repository', and you should see 0 changes to commit.

## 4. To Post Updates

Create a new post in the _posts folder, or make changes to an existing one. After your edits, you should see at least a blue 1 on the Git icon in Code's Activity Bar.

To `commit` your changes in Code:

1. Click on the Git icon in the Activity Bar on the left.

1. Enter a `commit` message (Code requires it).

1. Either click the check mark at the top of the Git pane, or press `Ctrl+Enter`.

    You will now see that there are changes to `commit` in the status bar at the bottom of the Code window. This means that they are *staged*.

    Status bar showing one committed update:

    ![".png image of Code status bar before changes"]({{ site.baseurl }}/images/code-after-repo-edits.png)

To `push` changes up to your GitHub repo with Code:

1. In the status bar at the bottom of the window, click the right number next to 'master' (see image just above). It has an upward arrow next to it, indicating that you have an update that is not pushed yet.

1. A bar will appear at the top of Code, stating: This action will push and pull commits to and from 'origin/master'. Note that 'origin' is the remote repo, and 'master' is your local copy. Click 'OK'. You'll get a GUI pop-up asking for your username and password. The status bar at the bottom of Code will change to reflect that there are no commits staged for pushing.

    Status bar after committing and pushing all changes to your GitHub repo:

    ![".png image of Code status bar after changes"]({{ site.baseurl }}/images/code-before-repo-edits.png)

Note that updates can take a few minutes when you view your changes from github.io.

## 5. To Add New Files to Your Repo

To add new files to your online repo that weren't created in Code, like a new post would be (e.g., an image file or other resource), you must use a terminal, because VS Code is not aware of the new files with regard to git. In the following example, I placed two new image files in my /images folder in my local repository that I wished to link in a post. Then, using a terminal, or in the Code's terminal (View, Integrated Terminal in Code):

1. `cd` to the root of the local repo if you are not already there (regardless of where the new files are).

1. Issue the `add` 'all' command to stage the changes:

        hikinthru.github.io$ git add .

1. Commit the changes with a commit message in quotes:

        hikinthru.github.io$ git commit -m "Add two images"

    You should see a confirmation like this:

        [master 950dd22] Add two images
        2 files changed, 0 insertions(+), 0 deletions(-)
        create mode 100644 images/code-after-repo-edits.png
        create mode 100644 images/code-before-repo-edits.png

1. Your changes are now committed. To `push` them up:

        hikinthru.github.io$ git push origin master

    After entering your username and password, you should see a confirmation:

        Counting objects: 9, done.
        Delta compression using up to 2 threads.
        Compressing objects: 100% (9/9), done.
        Writing objects: 100% (9/9), 6.32 KiB | 0 bytes/s, done.
        Total 9 (delta 5), reused 0 (delta 0)
        remote: Resolving deltas: 100% (5/5), completed with 4 local objects.
        To https://github.com/hikinthru/hikinthru.github.io
        1299a3e..950dd22  master -> master
