Lab 4: Git and GitHub Basics
================
Gaston Sanchez

> ### Learning Objectives
> 
>   - Create a GitHub repository
>   - Create a local Git repository
>   - Practice adding, and committing changes to your (local) Git repo
>   - Practice pushing committed changes to a remote repo

### General Instructions

  - This lab involves 3 parts:
    1.  GitHub workshop
    2.  Git and GitHub Practice
    3.  Your GitHub Classroom repository
  - We assume that you have installed Git in your computer, and that you
    created a GitHub account.
  - Write your descriptions, explanations, and code for the frist two
    parts in an `Rmd` (R markdown) file.
  - Name this file as `lab04-first-last.Rmd`, where `first` and `last`
    are your first and last names (e.g. `lab04-gaston-sanchez.Rmd`).
  - Knit your `Rmd` file as an html document (default option).
  - Submit your `Rmd` and `html` files to bCourses, in the corresponding
    lab assignment.
  - Due date displayed in the syllabus (see github repo).

-----

## Part 1) Git Workshop

The first part of the lab involves working on the workshop [Version
Control with Git](http://swcarpentry.github.io/git-novice/) by *Software
Carpentry*, especifically parts 3 to 7 (I’m assuming that you have Git
setup in your machine).

The next step is to introduce yourself to Git by running a couple of
configuration commands. Basically, you need to tell Git who you are, and
what your email is. Run the following commands using **your own user
name** and you **own email**.

``` bash
# use your own user name
git config --global user.name "Gaston Sanchez"

# use your own email
git config --global user.email "gasigiri@berkeley.edu"

# colors
git config --global color.ui "auto"
```

### Your turn

Write your bash commands inside one or more code chunks that are NOT
evaluated. One way to do this is to add the option `eval = FALSE` inside
the curly braces of the chunk (see image below)

![](lab03-images/unevaluated-chunk.png)

2.  [Setting Up Git](http://swcarpentry.github.io/git-novice/02-setup/)
3.  [Creating a
    Repository](http://swcarpentry.github.io/git-novice/03-create/)
4.  [Tracking
    Changes](http://swcarpentry.github.io/git-novice/04-changes/)
5.  [Exploring
    History](http://swcarpentry.github.io/git-novice/05-history/)
6.  [Ignoring
    Things](http://swcarpentry.github.io/git-novice/06-ignore/)
7.  [Remotes in
    GitHub](http://swcarpentry.github.io/git-novice/07-github/)

-----

## Part 2) Git and GitHub Practice

The second part of the lab involves working on a second baby project
with Git. Here are some resources that you may find useful:

  - Chapters 1 **Getting Started**, and sections 2.1 to 2.5 in chapter 2
    **Git Basics**, of the [Pro Git](https://git-scm.com/book/en/v2) by
    Scott Chacon and Ben Straub.

  - [Github Git Cheat
    Sheet](https://education.github.com/git-cheat-sheet-education.pdf)

### 1\) Create a New GitHub Repository

  - Open your browser and Sign in to your github account.
  - Locate the `+` button (next to your avatar).
  - Select the `New repository` option.
  - Choose a name for your repository: e.g. `demo-repo`.
  - In the **Description** field add a brief description: e.g. “this is
    a demo repo”
  - Use the default settings, and click the green button **Create
    repository**.
  - You should see some content similar (but not identical) to the one
    below:

<!-- end list -->

``` bash
echo "# Demo Repo" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/gastonstat/demo-repo.git
git push -u origin master
```

### 2\) Create a local Git Repository

  - Open the terminal (Mac Terminal, or Git-Bash for Windows users).
  - Optional: change directory to your preferred location e.g. your
    `Desktop`

<!-- end list -->

``` bash
cd Desktop
```

  - Create a directory with the name of your github repo

<!-- end list -->

``` bash
mkdir demo-repo
```

  - Change to the directory you just created

<!-- end list -->

``` bash
cd demo-repo
```

  - Initialize the directory as a git repository

<!-- end list -->

``` bash
git init
```

It’s possible that you encounter some error message, e.g. Mac users may
get a message related with a missing component for `CommandLineTools`.
If this your case, then type in the terminal console:

``` bash
# Mac users may need to run this command
xcode-select --install
```

The command `git init` will set-up your directory `demo-repo` as a Git
repository (NOT to confuse with your GitHub repository). This is
basically your **local** repository.

### 3\) Adding a README file

  - It is customary to add a `README.md` file at the top level. This
    file must contain (at least) a description of what the repository is
    about. The following command will create a `README.md` file with
    some minimalist content:

<!-- end list -->

``` bash
echo "# Demo Repo" >> README.md
```

  - So far you have a “new” file in your local repo, but this change has
    not been recorded by Git. You can confirm this by checking the
    status of the repo:

<!-- end list -->

``` bash
git status
```

  - Notice that Git knows that `README.md` is untracked. So let’s add
    the changes to Git’s database:

<!-- end list -->

``` bash
git add README.md
```

  - Check the status of the repo again:

<!-- end list -->

``` bash
git status
```

  - Now Git is tracking the file `README.md`.
  - Next thing consists of **committing** the changes. It’s always a
    good practice to include a meaningful message for your commit.

<!-- end list -->

``` bash
git commit -m "first commit"
```

### 4\) Adding a remote

Right now you have a (local) Git repository in your computer. And you
also have a (remote) GitHub repository in your GitHub account. Both
repositories should have the same name, and the goal is to link them. To
do this, you need to tell Git that a *remote* repository (i.e. the one
in GitHub) will be added:

  - To add a remote repository use the command below **with your own
    username**:

<!-- end list -->

``` bash
git remote add origin https://github.com/username/demo-repo.git
```

  - Verify your new remote

<!-- end list -->

``` bash
git remote -v
```

  - If everything is okay, you should be able to see a message (with
    your own username) like this:

<!-- end list -->

    # Verify new remote
    origin  https://github.com/username/demo-repo.git (fetch)
    origin  https://github.com/username/demo-repo.git (push)

### 5\) Pushing changes to a remote repo

  - Now that you have linked your local repo with your remote repo, you
    can start pushing (i.e. uploading) commits to GitHub.
  - As part of the basic workflow with git and github, you want to
    constantly check the status of your repo

<!-- end list -->

    git status

  - Now let’s push your recent commit to the remote branch (`origin`)
    from the local branch (`master`):

<!-- end list -->

``` bash
git push origin master
```

  - Go to your Github repository and refresh the browser. If everything
    went fine, you should be able to see the contents of your customized
    `README.md` file.
  - Keep modifying the content of `README.md` file, `add` the
    modifications to the git repository, display the `status`, `commit`
    the modifications, and `push` them to github repo.

-----

## Part 3) Your GitHub Classroom Repository

The last part of the lab involves setting up your **GitHub Classroom**
repository. Please follow the instructions of the pdf (shown below),
available in the `labs/` folder of the course github repo:

[lab04-github-classroom.pdf](lab04-github-classroom.pdf)

You don’t need to include descriptions or code of this 3rd part in your
`.Rmd` lab.
