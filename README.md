# git and Github basics

- [Setting up](#setting-up)
- [`git init`](#git-init)
- [`git clone`](#git-clone)
- [`git remote`](#git-remote)
- [`git checkout`](#git-checkout)
- [`git add`](#git-add)
- [`git commit`](#git-commit)
- [`git push`](#git-push)
- [`git status`](#git-status)
- [`git log`](#git-log)
- [`git show`](#git-show)
- [`git diff`](#git-diff)
- [`git fetch`](#git-fetch)
- [`git branch`](#git-branch)
- [`git pull`](#git-pull)
- [`git merge`](#git-merge)
- [`git cherry-pick`](#git-cherry-pick)
- [`git reset`](#git-reset)

---

## Introduction

![xkcd knows](https://imgs.xkcd.com/comics/git.png)

`git` is a **system to keep track of changes** across a set of files in a folder on your computer. It lives in a hidden folder called `.git` and it keeps track of all changes specified, as you work.

Every change, or **commit**, has a unique ID (or **hash**) linked to its parent. Furthermore, you can create **branches**, which have a different history than your master branch, with their own commits; these can then be merged back into the master.

`git` may also use a file called `.gitignore`; this file contains paths to those files and folders which need not be tracked. These files include virtual environments, IDE-specific build files, and so on. The simplest way to get an inclusive `.gitignore` file is to generate one on [gitignore.io](https://www.gitignore.io/) -- just enter the development environment you want (eg, `Python`), hit *Create*, and save the output into the `.gitignore` file in your project folder.

**[github.com](https://github.com/)** is **not** `git`; it is simply a convenient website to backup and share your repositories, via the `git` protocol.

![Git flow](./git-flow.svg)

---

## Installation

At this point you should have `git` already installed. If for whatever reason you do not, you will need to install `git` by running these commands in a terminal:

```sh
$ sudo apt-get update
$ sudo apt-get install git-all
```

This will make sure you have the latest sources for the software to be installed, and then install `git` for your system, if it's not already present.

Please note that you will have to provide your system password for `sudo` commands.

---

## Preamble

Below you will find the [list of git commands](#commands), the typical workflow for [creating a new project](#creating-a-new-project) as well as the workflow for [contributing to an existing project](#contributing-to-an-existing-project).

The commands to be typed in the terminal will show up like this:

```bash
$ git log
```

(The `$` indicates the prompt)

Please note that the text in `<angle brackets>` should be replaced with your own text. Aditionally, text in `[square brackets]` is optional, i.e. you can skip it.

The sample output of a command will show up like this:

> ```bash
> commit 21316f2eb86c30402ff5cd4598c910906c1d32ad (HEAD -> master)
> Author: alexsincai <alex.sincai@yahoo.co.uk>
> Date:   Tue Feb 25 10:22:04 2020 +0200
>
>     Added Readme
> ```

[Back to top](#git-and-github-basics "to top")

---

## Creating a new project

Let's start by creating a new project. Create a new folder and add some content.

Before starting any actual work, start by initializing `git` in the current folder; you do this by running `git init` in the terminal. Then, create your first commit, by running `git add .` followed by `git commit -m "First commit"`.

This will track all files in the current folder.

Then, create a remote repository, by navigating to your github page and [creating a new repository](https://github.com/new). Give it a name, a description, and click "Create".

Once you have the repository, go to your folder and connect it to the remote repository; you do this by running `git remote add origin <repo URL>`.

Finally, run `git push -u origin master` to send the files from your *local* repository to the *remote* repository.

To recap:

1. Navigate to your folder
2. `git init`
3. Modify / add files
4. `git add <all relevant files>`
5. `git commit -m "Commit message"`
6. Create a repo on github
7. `git remote add origin <repo URL>`
8. `git push -u origin master`
9. Repeat steps 3, 4, 5, 8 as needed

[Back to top](#git-and-github-basics "to top")

---

## Contributing to an existing project

In CodeCool, most repositories will be automatically created for you. Thus, to work on your project, navigate to the project's repo URL and clone it with `git clone <URL>`. Create a new branch with `git checkout -b <new branch name>` and then get all the content -- you do this using `git pull`.

Proceed to make all required changes. Add the changed files with `git add <list of files>`, commit with the relevant message (`git commit -m "<message>"`), and push the branch (`git push -u origin <branchname>`).

Then, go to the github page of the project, click the "Pull requests" tab, and hit the "New pull request" button. Compare the `base: master` with the `compare: <branch name>` and click "Create pull request". Fill in the details, and click "Create pull request" again.

If you see any conflicts, resolve them, otherwise wait for the repo owner to merge your changes.

To recap:

1. `git clone <URL>`
2. `git checkout -b <new branch name>`
3. `git pull`
4. Make the necessary changes
5. `git add <files>`
6. `git commit -m "<descriptive message>"`
7. `git push -u origin <branch name>`
8. Create a new pull request with a descriptive message
9. Solve any conflicts
10. Wait for the repo owner to merge your changes

---

## Commands

### Setting up

`git` (and github) needs to know about you. Unfortunately, this is a rather more complex process than it used to be.

First, you will need to set up **2FA** (Two-Factor Authentication). For that, you will need a smartphone on which you must install [Google Authenticator](https://play.google.com/store/apps/details?id=com.google.android.apps.authenticator2&hl=en_US&gl=US). This will generate a new access token every time you open the app.

Then, go to your github settings page, and under Developer settings, select [Personal access tokens](https://github.com/settings/tokens), and click on the **New access token** button on the right side. When prompted, check **repo**, **admin:repo_hook** and **delete_repo**, then cick the green **Generate token** button. This will provide a new access token.

> ## Save this token somewhere safe, where you can recover it later

Next to the field where you get the token, you will see a drop-down labelled **Enable SSO**. Make sude you select "Enable SSO", and select *github* as the authorized organisation.

Once you've done this, go to [this page](https://docs.github.com/en/get-started/getting-started-with-git/caching-your-github-credentials-in-git) and follow the instructions for your operating system.

[Back to top](#git-and-github-basics "to top")

---

### `git init`

Create or navigate to the folder where you will work, then initialize git

```bash
$ git init
```

[Back to top](#git-and-github-basics "to top")

---

### `git clone`

Allows you to clone a remote repository to your machine.

```bash
$ git clone <remote repository> [<local folder>]
```

Should there be several remotes (`git remote -v`), you can specify which non-origin remote you want to clone, otherwise "origin" will be used.

> ```bash
> Cloning into 'git-github-presentation'...
> remote: Enumerating objects: 37, done.
> remote: Counting objects: 100% (37/37), done.
> remote: Compressing objects: 100% (26/26), done.
> remote: Total 37 (delta 11), reused 33 (delta 7), pack-reused 0
> Unpacking objects: 100% (37/37), done.
> ```

[Back to top](#git-and-github-basics "to top")

---

### `git remote`

Lets the local repository know about the remote repository

```bash
$ git remote add origin <URL>
```

As stated above, the name of the remote can be something other than **origin**, but it is that by convention; changing this will cause headaches down the road.

This command also allows one to set *several* remotes, for any number of reasons, most commonly to separate development and deployment servers.

To check if there are several remotes, use:

```bash
$ git remote -v
```
To add a new remote:

```bash
$ git remote add <new remote name> <new URL> 
```

**When cloning from a non-origin remote, please specify this remote's name!**

[Back to top](#git-and-github-basics "to top")

---

### `git checkout`

This sets the HEAD to a specified commit hash or branch

To work on a previous commit:

```bash
$ git checkout <hash>
```

> ```bash
> Note: checking out '21e40ae300061b7849417f9bc8de783ebb17c7ba'.
>
> You are in 'detached HEAD' state. You can look around, make experimental
> changes and commit them, and you can discard any commits you make in this
> state without impacting any branches by performing another checkout.
>
> If you want to create a new branch to retain commits you create, you may
> do so (now or later) by using -b with the checkout command again. Example:
>
>  git checkout -b <new-branch-name>
>
> HEAD is now at 21e40ae Added style
> ```

To work on a different branch:

```bash
$ git checkout <branch>
```

> ```bash
> Switched to branch 'color'
> Your branch is up to date with 'origin/color'.
> ```

You can also create a new branch and work on it with:

```bash
$ git checkout -b <new branch name>
```

> ```bash
> Note: checking out '21e40ae300061b7849417f9bc8de783ebb17c7ba'.
>
> You are in 'detached HEAD' state. You can look around, make experimental
> changes and commit them, and you can discard any commits you make in this
> state without impacting any branches by performing another checkout.
>
> If you want to create a new branch to retain commits you create, you may
> do so (now or later) by using -b with the checkout command again. Example:
>
> git checkout -b <new-branch-name>
>
> HEAD is now at 21e40ae Added style
> ```

[Back to top](#git-and-github-basics "to top")

---

### `git add`

Let git know about new / modified files

To add a single file:

```bash
$ git add <file>
```

To add several files:

```bash
$ git add <file 1> <file 2> ... <file n>
```

To add the current folder:

```bash
$ git add .
```

[Back to top](#git-and-github-basics "to top")

---

### `git commit`

Have git track the desired files

```bash
$ git commit -m "<descriptive message>"
```

[Back to top](#git-and-github-basics "to top")

---

### `git push`

This syncs the current local branch to the remote repository, on the same branch

```bash
$ git push --set-upstream origin <branch>
```

...which can be shortened to

```bash
$ git push -u origin <branch>
```

Please note that **origin** is just a label, it can be called anything (but really shouldn't...). "origin" is just the standard name for the remote repo's URL.

```bash
$ git push
```

[Back to top](#git-and-github-basics "to top")

---

### `git status`

See the status of the files (untracked, new, modified, deleted) on the current branch

```bash
$ git status
```

> ```bash
> On branch master
> Changes not staged for commit:
>   (use "git add <file>..." to update what will be committed)
>   (use "git checkout -- <file>..." to discard changes in working directory)
>
> 	modified:   README.md
>
> Untracked files:
>   (use "git add <file>..." to include in what will be committed)
>
> 	.gitignore
>
> no changes added to commit (use "git add" and/or "git commit -a")
> ```

[Back to top](#git-and-github-basics "to top")

---

### `git log`

For the current branch, it shows the **commit hash**, author's **name** and **email**, the **date** and the **commit message**

```bash
$ git log
```

> ```bash
> commit 56ead357b1a24f791cce3678883f8407a234585f (HEAD -> master)
> Author: alexsincai <alex.sincai@yahoo.co.uk>
> Date:   Tue Feb 25 10:25:07 2020 +0200
>
>     Updated Readme
>
> commit 21316f2eb86c30402ff5cd4598c910906c1d32ad
> Author: alexsincai <alex.sincai@yahoo.co.uk>
> Date:   Tue Feb 25 10:22:04 2020 +0200
>
>     Added Readme
> ```

[Back to top](#git-and-github-basics "to top")


---

### `git show`

Shows the details of a certain commit

```bash
$ git show <hash>
```

> ````diff
> $ git show 76b66dd4fd566f21a5f1f444a733202418d866f3
> commit 76b66dd4fd566f21a5f1f444a733202418d866f3 (HEAD -> master)
> Author: alexsincai <alex.sincai@yahoo.co.uk>
> Date:   Tue Feb 25 10:28:53 2020 +0200
>
>     Rephrased a line
>
> diff --git a/README.md b/README.md
> index 7612fe6..34ae635 100644
> --- a/README.md
> +++ b/README.md
> @@ -237,7 +237,7 @@ $ git log
>
>  ### `git show`
>
> -Shows the details of your commit
> +Shows the details of a certain commit
>
>  ```bash
>  $ git show <hash>
> ````

[Back to top](#git-and-github-basics "to top")

---

### `git diff`

When a local file contains changes that do not exist remotely, `diff` will show the differences between versions.

```bash
$ git diff
```

```bash
$ git diff <file>
```

> ```diff
> diff --git a/style.css b/style.css
> index 1bbf05f..33f3834 100644
> --- a/style.css
> +++ b/style.css
> @@ -5,7 +5,5 @@ body {
> }
>
> h1 {
> -
> -color:burgundy;
> -
> -}
> \ No newline at end of file
> +  color: burgundy;
> +}
> ```

[Back to top](#git-and-github-basics "to top")

---

### `git fetch`

Gets the content from the remote repository, **without** applying it.

```bash
$ git fetch
```

[Back to top](#git-and-github-basics "to top")

---

### `git branch`

See the list of branches on your repository, or create new ones

Used without arguments, it lists the local branches:

```bash
$ git branch
```

> ```bash
>  color
> * master
> ```

The **\* asterisk** shows the current branch.

Used with the **-a** argument, it also lists the branches that exist remotely:

```bash
$ git branch -a
```

> ```bash
>  color
> * master
>  remotes/origin/HEAD -> origin/master
>  remotes/origin/color
>  remotes/origin/master
> ```

Note the HEAD: it shows that the current branch _for the remote repository_ is the same as the current local branch.

To create a new branch, use

```bash
$ git branch <new name>
```

[Back to top](#git-and-github-basics "to top")

---

### `git pull`

Fetches and merges changes from the remote to the specified branch

```bash
$ git pull origin <name>
```

> ```bash
> From https://github.com/alexsincai/git-github-presentation
> * branch            master     -> FETCH_HEAD
> Updating 21e40ae..78b5fbd
> Fast-forward
> index.html | 2 +-
> style.css  | 8 ++++++++
> 2 files changed, 9 insertions(+), 1 deletion(-)
> ```

[Back to top](#git-and-github-basics "to top")

---

### `git merge`

Incorporates fetched changes into the current branch

```bash
$ git merge
```

To incorporate a certain commit, use

```bash
$ git merge <hash>
```

[Back to top](#git-and-github-basics "to top")

---

### `git cherry-pick`

So you've made your changes, pushed them, and the you notice that **OH NO! You've pushed to the wrong branch!**

`git cherry-pick` solves this issue; it incorporates a commit on a different branch into the current one.

```bash
$ git cherry-pick <commit ID>
```

First get a `git log` to see the exact commit id:

> ```bash
> commit ce2724ded4afeb6b1b89ece009216f25de477ec8 (HEAD -> master, origin/master, origin/HEAD)
> Author: alexsincai <alex.sincai@yahoo.co.uk>
> Date:   Tue Mar 3 10:21:40 2020 +0200
> 
>     Beautified code
> ```

Copy the commit ID, then `git checkout <correct branch>`, and `git cherry-pick <the copied ID>`.

If you run `git log` again on this branch, you will see the new commit:

> ```bash
> commit 95c6adadda16217de664303c738b3df9c757f7b4 (HEAD -> python)
> Author: alexsincai <alex.sincai@yahoo.co.uk>
> Date:   Tue Mar 3 10:21:40 2020 +0200
> 
>     Beautified code
> 
> commit df9edeac86bac23782cd537cf33e4a99474aef0e (origin/python)
> Author: alexsincai <alex.sincai@yahoo.co.uk>
> Date:   Tue Feb 25 11:38:19 2020 +0200
> 
>     Added python files
> ```

Cool, but the wrong changes still show up. You solve this using the next command.

[Back to top](#git-and-github-basics "to top")

---

### `git reset`

`git reset` allows you to "go back in time" to just before the error appeared, or rather, to the commit specified.

```bash
$ git reset <commit ID>
```

```bash
$ git reset --hard <commit ID>
```

```bash
$ git reset --soft <commit ID>
```

A reset can be *soft*, *mixed* (this is the default), or *hard*. A soft reset adds and commits the changes made for the specified commit; a mixed reset adds the changed files, but does not change them; a hard reset removes all the changes.

> ```bash
> commit ce2724ded4afeb6b1b89ece009216f25de477ec8 (origin/master, origin/HEAD)
> Author: alexsincai <alex.sincai@yahoo.co.uk>
> Date:   Tue Mar 3 10:21:40 2020 +0200
> 
>     Beautified code
> 
> commit 679e7b6d41a0625d5d8ea9366caca3e3da2ca944
> Author: alexsincai <alex.sincai@yahoo.co.uk>
> Date:   Tue Mar 3 10:00:21 2020 +0200
> 
>     URL didn't work
>
> $ git reset --hard 679e7b6d41a0625d5d8ea9366caca3e3da2ca944
> Unstaged changes after reset:
> M	area_of_circle.py
> 
> $ git log
> commit 679e7b6d41a0625d5d8ea9366caca3e3da2ca944 (HEAD -> master)
> Author: alexsincai <alex.sincai@yahoo.co.uk>
> Date:   Tue Mar 3 10:00:21 2020 +0200
> 
>     URL didn't work
> ```

[Back to top](#git-and-github-basics "to top")

---

