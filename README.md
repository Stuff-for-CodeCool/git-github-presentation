# git and Github basics

- [Introduction](#introduction)
- [Installation](#installation)
- [Please note that you will have to provide your system password for `sudo` commands.](#please-note-that-you-will-have-to-provide-your-system-password-for-sudo-commands)
- [Preamble](#preamble)
- [Contributing to an existing project](#contributing-to-an-existing-project)
- [Commands](#commands)
  - [Setting up](#setting-up)
  - [`git clone`](#git-clone)
  - [`git remote`](#git-remote)
  - [`git checkout`](#git-checkout)
  - [`git add`](#git-add)
  - [`git commit`](#git-commit)
  - [`git push`](#git-push)
  - [`git status`](#git-status)

---

## Introduction

`git` is a **system to keep track of changes** across a set of files in a folder on your computer. It lives in a hidden folder called `.git` and it keeps track of all changes specified, as you work.

Every change, or **commit**, has a unique ID (or **hash**) linked to its parent. Furthermore, you can create **branches**, which have a different history than your master branch, with their own commits; these can then be merged back into the master.

`git` may also use a file called `.gitignore`; this file contains paths to those files and folders which need not be tracked. These files include virtual environments, IDE-specific build files, and so on. The simplest way to get an inclusive `.gitignore` file is to generate one on [gitignore.io](https://www.gitignore.io/) -- just enter the development environment you want (eg, `Python`), hit *Create*, and save the output into the `.gitignore` file in your project folder.

**[github.com](https://github.com/)** is **not** `git`; it is simply a convenient website to backup and share your repositories, via the `git` protocol.

![Git flow](./git-flow.svg)

---

## Installation

On Ubuntu systems, you will need to install `git` by running these commands in a terminal:

```sh
$ sudo apt-get update
$ sudo apt-get install git-all
```

This will make sure you have the latest sources for the software to be installed, and then install `git` for your system, if it's not already present.

Please note that you will have to provide your system password for `sudo` commands.
--

## Preamble

Below you will find the [list of git commands](#commands) and the typical workflow for [contributing to an existing project](#contributing-to-an-existing-project).

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

[Back to top](#git-and-github-basics "to top")

---

## Commands

### Setting up

`git` (and github) needs to know about you. Run these commands to configure it:

```bash
$ git config --global credential.helper store
$ git config --global user.name "<github username>"
$ git config --global user.email "<github email adress>"
$ git config --global user.password "<github password>"
```

[Back to top](#git-and-github-basics "to top")

---

### `git clone`

Allows you to clone a remote repository to your machine.

```bash
$ git clone <remote repository> [<local folder>]
```

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
