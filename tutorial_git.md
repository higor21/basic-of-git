# A Git Explanation

The first thing you have to do is to download the Git in your machine:
[link to download](https://git-scm.com/downloads)

After that, you have to follow the under steps:

## How to configure the Git:

- `git config --global user.name <your name>`
- `git config --global user.email <your email>`

## Initialize Git:

- `git init`

The command above will create a directory called **.git**, that save all the configuration details.

## Main Concepts and Commands in Git

Now, you'll see the main concepts/commands, such as visualization of commits, refactory to previous version, work with branch and so on.

### > The general about Git

As you can see in the following image, there are four states in the Git:

- **Untracked:** Here, the files weren't saw by Git. To make it visible, you have to run
  `git add <name of files>` or `git add .`, this last one is to add all untracked files.
- **Unmodified:** As you can guess, the files weren't modified yet.
- **Modified:** Here, the files were modified, so you can now add them to 'staged' state.
- **Staged:** In this case, the files are ready to be commited

![git explanation image](./assets/git-general.png)

### > Visualization of Commits

To see the commits, you can just write `git log`. But if you want to see more information, type `git log --decorete`.

- **log with author filter:** `git log --author=<name or part of name of author>`
- **visualization of contribution:**

  _ `git shortlog`: shows the authors, the amount of commits from each author and their respective commits.
  
  _ `git shortlog -sn`: shows only the authors of commits and their amount of commits.
  
  _ `git shortlog --graph`: shows graphically how are the branchs
  
  _ `git show <hash>`: shows a specific commit
  
  _ `git diff`: shows what were your changes before commit the files
  
  _ `git diff --name-only`: this shows only the changed files before the commit

### > Refectory to Before Version

If you modify a file, but didn't want to do it, you can recover the previous state. This section is about it.

- `git checkout <name of file>`: you can recover from **modified** to **unmodified** file.
- `git reset HEAD <name of file>`: after you add the files, it can be recovered from **staged** to **modified** with this command
- `git reset --<option> <hash>`: This command has three options:
  _ `soft`: reset the commit to **staged** area, just before it be commited
  _ `mixed`: reset the commit to **modified** area \* `hard`: clear the commit, coming back to previous version

Obs.: As the `git reset --hard <hash>` command clear the commit and change the history, it can cause troubles in the future. Thus, it can't be used after a `git push` command.

### > A Remote Repository

The remote repository is a way to post your codes on the cloud. In this case, you can access it by Web, for example. The most popular online repository is the [GitHub](https://github.com/), which I'll explain to you how it works.

Once you have an account in it, you have to create a SSH key following the [tutorial]([https://help.github.com/en/articles/connecting-to-github-with-ssh](https://help.github.com/en/articles/connecting-to-github-with-ssh) to access your online repositories.

After you had configured your GitHub account, link you local git with your online git executing the following command:

`git remote add origin <link of online repository>`

To check it, use `git remote` and you should see the output `origin`

After that, use the push command to send your local files to the online repository as following:

`git push -u origin master`:

- push: send your datas
- -u: when you don't want code all the times `origin master` to push your datas, use it
- origin: to
- master: from

### > Difference between the 'clone' and 'fork':

The `clone` command is usually used to clone a repository to your machine, but you cannot cheate a `pull request`, as with the `fork` concept.
To make a clone, you have to do `git clone <name of repository>`

### > Manage Branchs:

A 'branch' is a pointer to specific commit, this is, a "local" to put your changes without break other people changes.

- **Create a new branch:** `git checkout -b <name of new branch>`
- **Change the local branch:** `git checkout <name of branch>`
- **Delete a local branch:** `git checkout -D <name of branch>`

You can also use `merge` or `rebase` when working with branchs. Both the cases, you are merging one branch to another. The difference between it, is that `merge` command makes a new commit saving the commits' history, while the other one mix the history, putting the commit of one branch in front other branch's commit.

`git merge/rebase <name of another branch>`

Example: Imagine you're in B1 branch and you want to merge it to B2 branch. So, you have to do `git merge B2`

### > Project versioning on Git:

If you want to save each step from your project, declaring each version of it, you can manage it with the tags concept.

Commands:

- `git tag -a <version> -m "<mensage>"`: create a tag
- `git tag`: check created tags
- `git push origin master --tags`: commant to send all the tags to remote version
- `git tag -d <name of tag>`: delete tag from local repository

### > Other utilities:

- Reverting the commit to save what you changed, before using reset command. Thus, it isn't possible to break the application and save what you did, at the same time.
  `git revert <hash of commit>`
- Deleting a branch or tag from remote repository:
  `git push origin :<name of branch or tag>`
  or
  `git push origin --delete <name of branch or tag>`
