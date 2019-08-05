# A Git Explanation


The first thing you have to do is to download the Git in your machine:
[link to download](https://git-scm.com/downloads)

After that, you have to follow the under steps: 

## How to configure the Git:

* `git config --global user.name <your name>`
* `git config --global user.email <your email>`

## Start in Git:

* `git init`

The command above create a directory called **.git**, that save all the configuration details.

## Means Concepts and Commands in Git

Now, you'll see the mean concepts/commands, as visualization of commits, refectory to before version, work with branch and so on. 

### > The general about Git

As you can see in the following image, there are four states in the Git:
* **Untracked:** Here, the files wasn't saw by Git. To make it, you have to do 
`git add <name of files>` or `git add .`, this is to add all untracked files
* **Unmodified:** As you can guess, the files wasn't modified yet.
* **Modified:** Here, as the files was modified, you can now add them to 'staged' state.
* **Staged:** In this case, the files are ready to be commited

![git explanation image](git-general.png)

### > Visualization of Commits

To see the commits, you can write `git log` only. But if you want to see more information, tap `git log --decorete`.

* **log with author filter:** `git log --author=<name or part of name of author>`
* **visualization of contribution:** 
	* `git shortlog`: shows the authors, the quantity of commits from each author and their respective commits.
	* `git shortlog -sn`: shows only the authors of commits and their quantity of commits.
	* `git shortlog --graph`: shows graphically how are the branchs
	* `git show <hash>`: shows a specific commit
	* `git diff`: shows what ware your changes before commit the files
	* `git diff --name-only`: this shows only the changed files before the commit

### > Refectory to Before Version

If you modify a file, but didn't want to do it, obvious, you can recover the before state. This section treats about it.

* `git checkout <name of file>`: you can recover from **modified** to **unmodified** file. 
* `git reset HEAD <name of file>`: after you add the files, them can be recovered from **staged** to **modified** with this command
* `git reset --<option> <hash>`: This command has three options:
	* `soft`: reset the commit to **staged** area, just before to be commited
	* `mixed`: reset the commit to **modified** area
	* `hard`: clear the commit, coming back to before version

Obs.: As the `git reset --hard <hash>`clear the commit and change the historic, it can cause troubles in the future. Thus, it can't be used after a `git push` command.

### > A Remote Repository

The remote repository is a way to post your codes on the cloud. In this case, you can access it by Web, for example. The most popular online repository is the [GitHub](https://github.com/), which I'll explain you how it works.

Once you have a account in it, you have to create a SSH key folloing the [tutorial]([https://help.github.com/en/articles/connecting-to-github-with-ssh](https://help.github.com/en/articles/connecting-to-github-with-ssh) to access your online repositories.

After you had configured your GitHub account, link you local git with your online git adding the following command:

`git remote add origin <link of online repository>`

To check it, use `git remote` and you should see the output `origin`

After, use the push command to send your local files to online repository as following:

`git push -u origin master`:
* push: send your datas
* -u: when you don't want code all the times `origin master` to push your datas, use it
* origin: to
* master: from

### > Difference between the 'clone' and 'fork': 
	
The `clone` command is usually used to clone a repository to you, but you cannot cheate a `pull request`, as with the `fork` concept. 
To make a clone, you have to do `git clone <name of repository>`

### > Manage Branchs:

A 'branch' is a pointer to specific commit, this is, a "local" to put your changes without break other people changes. 

* **Create a new branch:** `git checkout -b <name of new branch>`
* **Change the local branch:** `git checkout <name of branch>`
* **Delete a local branch:** `git checkout -D <name of branch>`
