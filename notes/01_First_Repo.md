# Our First Repository

## DevOps and Git in a Nutshell

**DevOps** basically means modern software development practices and **Git** is a version control system. 

A key principle of DevOps is to improve code in small steps which leads to continuous improvement. Let's now see how Git helps us to improve code:

- Git manages versions of project, where each version is called a **commit**.
- Git is highly efficient where each commit is a snapshot of the entire project but it doesn't store multiple copies, instead it only keeps unique files.
- A collection of commits is called history, and we can review or undo changes in a history.
- All commits belong to a branch where a branch is an independent line of development of the project. By default, we have a **master** branch.
- **Branches** help us maintain a stable version while we are continuously changing the code.
- When a branch is all tested, it's ready to be merged into the master branch. **Pull Request** is a request to merge one branch into another branch. This often results in intensive reviewing of the new code.

In short, Git helps in:

- **Continuous Improvement via commits**
- **Simultaneous stability and development via branches**
- **Improved quality via pull requests**

## Git Overview

Git is a distributed (local and remote repositories) version control system. A Git Repository contains a series of snapshots or commits of a project. Let's look at basic command line syntax for Git:

```shell
$ git [command] [--flags] [arguments]
```

For example:

```shell
$ git status
$ git status --short
$ git add file.txt
```

Git commands have several ques that helps reading them:

- `-f` or `--flag` are flags that change the command's behavior.
- `|` is or, which can be used to put multiple flags together.
- `[optional]`, optional arguments are put in square brackets.
- `<placeholder>`, placeholders are put in angle brackets.
- `()`, curved braces are used for grouping.
- `--` shows disambiguous command.
- `...` used for multiple occurrences.

For example:

```shell
$ git command (-p | --patch) [<id>] [--] [<paths>...]
```

Every git commit contains the username and email information, hence it's important to set that up properly at the start:

```shell
$ git config --global user.name "username"
$ git config --global user.email "email.com"
$ git config --global core.editor nano
```

> Here we are using `--global` flag which sets the config for all repos used by the current user. We can also use `--local` which will keep the configs isolated to the repository (this is used if nothing is passed) and `--system` which will set the configs to all user on the computer.

We can get the configs using the command `git config <key>`.

## Git Locations

Git has four main locations:

- **Working Tree:** Contains a single commit's directory and files. This is where we can view the code and make changes.
- **Staging Area:**  This contains the files planned to be included in the next commit. 
- **Local Repository:** All the commits of the project.
- **Remote Repository:** Located on the cloud.

> The first three are present in the project directory.
>
> ```markdown
> Project/
> ├─ Working Tree
> ├─ .git/ => This hidden directory contains Staging area and local repo
> ```

## Local Repository

`git init` initialises a repository:

```shell
~/dev/Version-Control
git init --initial-branch=master
Initialized empty Git repository in /Users/rvn/dev/Version-Control/.git/
```

Making `master` branch default:

```sh
~/dev/Version-Control git:(HEAD)
git config --global init.defaultbranch master
```

Let's now see how to commit changes to the repository:

- `git status` checks the status of the files in working tree and staging area.
- `git add` adds files to the staging area.

