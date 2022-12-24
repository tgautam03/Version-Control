# Branching and Merging 1

## Git's Graph Model

Git's graph model defines the relationship among the commits in a repository with a Directed Acyclic Graph. The arrows point at a commit's parent and branching occurs when a commit has more than one child, while merging occurs when a commit has more than one parents and one child. We can see graph using the following command:

```shell
git log --graph
```

## Git IDs

Internally git uses **objects** to store 4 types of things:

- **Commit Object:** A small txt file containing things like user's commit info (message, reference to commit's parent or root tree of project).
- **Annotated Tag:** Reference to a specific commit.
- **Tree:** Directories and filenames in the project.
- **Blob:** The content of the file in the project.

> User only interacts with commit objects and annotated tag.

A **Git ID** or **object ID** or **SHA-1** or **hash** or **checksum** (40 character hexadecimal string) is the name of a git object. We can see Git ID here (number after the word `commit` is ID):

```shell
git log
commit 125ab296ddfb6a66029799884d80b9cc84a384a2 (HEAD -> master, origin/master)
```

> We can generate SHA-1 for a file using command:
>
> ```shell
> git hash-object <filename>
> ```

40 character ID numbers are hard to work with, so we can shorten them using `--oneline` tag. 

## Git References

**Reference** is a user friendly name pointing to commit's SHA-1 value. Reference pointing to another reference is called symbolic reference.

```sh
git log
commit 125ab296ddfb6a66029799884d80b9cc84a384a2 (HEAD -> master, origin/master)
```

`HEAD -> master, origin/master` are the three references associated with this commit. 

Branch label (master) points to the most recent commit in the branch and is implemented as reference. 

HEAD is the reference to the current commit, and usually points to the label of the current branch.

Tag is label attached to a specific commit. They can be lightweighted or annotated. We can access tags using `git tag` command and also assign tag to a commit as follows:

```sh
git tag v0.1
```

This will assign v0.1 to the most recent commit. Annotated tag is created as follows:

```sh
git tag -a -m"Version 2 here" v2.0
```

`git push` will not transfer tags to the remote repo. We have to do that manually as follows:

```sh
git push origin --tags
```

## Branches

We can create a branch 

```sh
git branch <branch name>
```

Checkout switches the branch

```sh
git checkout <branch name>
```

`checkout` basically moves the HEAD. We can also checkout commits, which lead to detached HEAD.

We can delete branch label (will not delete commits) using

```sh
git branch -d <branch name>
```

> We can delete unmerged branched too using `-D` flag and can undo it by checkout into the dangling commit using `git reflog`.

## Merging

Merging combines two branches. 

### Fast Forward Merge

 Moves the base branch label to the tip of the topic branch. It is only possible if no changes are made to the base branch which work on topic branch is done. Steps to do FF merge:

- Checkout to base branch
- `git merge <topic branch>`
- `git branch -d <topic branch>`
