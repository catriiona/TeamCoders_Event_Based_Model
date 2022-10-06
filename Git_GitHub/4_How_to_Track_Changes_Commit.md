
# How to change files, make Commits and placed them in Git repos. 

To demonstrate changes in files using Unix Shell at the terminal and command line,  we create text files and use the **nano** as shown at the 2_Unix_shell.md section. If you have Markdown files (.md) you can use a Markdown editor (Jupyter notebooks, VSCode etc). If you use .doc files use word editor. All these editors operate out of the command line at the terminal window.  

Now create a text file called pizza.text using the nano editor. Write few lines and save it as indicated at the picture.

```bash 
cd cooking/recipes/food/
nano pizza.txt
```
Editor opens 

![pizza.txt](./fig/nano_pizza.png)

Then press *control O* to save (write out) and *Enter* when asked 'Filename to Write: pizza.txt'. Finally press *control X * to exit

Now you have a text file in the food folder
```bash
ls -a
```
**Output**
```bash
.		..		curry.md	pizza.md	pizza.txt
```



## 1st command git status
It is strongly recommended before you do anything else to run **git status** as below 

```bash 
$ git status
```
**Output**
``` bash 

On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	../.DS_Store
	../baking/
	./

nothing added to commit but untracked files present (use "git add" to track)
```

**git status** is a very useful command that we will use a lot. It should be your first point of call to figure out the current state of a repository and often suggests commands that can be used for different tasks.

Don’t worry about all the output for now, the important bit is that the 2 files we already have are untracked in the repository (directory). We want to add the files to the list of files tracked by Git. Git does not track any files automatically and you need make a conscious decision to add a file. Let’s do what Git hints at:

```bash
 $ git add pizza.txt
 $ git status
```

**Output**
```bash 
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   pizza.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	../.DS_Store
	../baking/
	curry.md
	pizza.md
```


Now this change  stages the file pizza.txt and ready to be committed. There is an option to unstage it using 
"git rm --cached pizza.txt..." but we dont want it here.
The files carry.md pizza.md (in the food directory) and the directory /bakind/ are not on stage!!


 Note that if we wanted to stage and commit all the files at once we could have saved some typing here with the command (git add carry.md pizza.md pizza.txt).

## git commit -m  (write message)
Let us now commit the change to the repository:
```bash 
$ git commit -m "write ingredients"
```
***Output**
```bash

[main (root-commit) f50fddc] write ingredients
 1 file changed, 24 insertions(+)
 create mode 100644 food/pizza.txt
 ```
 We have now finished creating the first snapshot in the repository. Named after the command we just used, a snapshot is usually referred to in Git as a commit, or sometimes a changeset. We will use the term commit from now on. Straight away query the status to get this useful command into our muscle memory:

 ```bash
 $ git status
 ```

 **Output**
 ```bash 
 On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	../.DS_Store
	../baking/
	curry.md
	pizza.md

nothing added to commit but untracked files present (use "git add" to track)
```
This shows that there are untracked changes at other files. If we want to keep everything committed in the first snap of the repository, we add and commit everything at once. run the following commands.

```bash 
git add curry.md pizza.md ../baking/
git commit -m "first changes"
```
**Output**
```bash 
[main cebdb2c] first changes
 4 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 baking/cake.md
 create mode 100644 baking/cookies.md
 create mode 100644 food/curry.md
 create mode 100644 food/pizza.md
 ```

 This shows that we are at the main (main) branch of the recipes repository and we have saved all the changes  at the directories baking and food: 
 baking/cake.md
 baking/cookies.md
 food/curry.md
 food/pizza.md
 under one commit "first changes" with a create mode 100644 

If we run again git status 
```bash 
git status
```
**output
```bash 
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	../.DS_Store

nothing added to commit but untracked files present (use "git add" to track)
```

The output we get now is very minimal. This highlights an important point about the status command - it’s purpose is to report on changes in the -recipes- repository relative to the last commit. In order to see the commits made in a project we can use:

## History of the commits with git log 
``` bash
$ git log
```

** Output**
```bash 
commit cebdb2ced222527abc2b062c804487e9c179bc6c (HEAD -> main)
Author: MaryT <m.tziraki@gmail.com>
Date:   Tue Feb 8 12:32:43 2022 +0000

    first changes

commit f50fddc8b03956ce453375c1cf5d5799e5ce7a51
Author: MaryT <m.tziraki@gmail.com>
Date:   Tue Feb 8 12:25:09 2022 +0000

    write ingredients


```
We’ll talk in more detail about the output here but for now the main point is to recognize that the commits have been created with your personal information and the message you specified.



# File changes, Staging and Committing.    

We saw that it is a two-step process for our first commit - first, we use git add, then git commit. This is an important pattern used by Git. To understand this in more detail, it’s useful to know that Git has three ‘areas’ shown in the following picture.

Our changes to a file move from our editor (working directory) to the staging area and into long-term storage at the repository. All the versions of the file and their commits are stored in the repository. Therefore version control can be done in the repository and not at our editor.

![staging](./fig/stage.png)


- The Working Directory (or Working Tree)
   - This is the copy of the files that you actually work with in a normal way.

-  The Staging Area (or index)
   - When you run git add a copy of a file is taken from the working tree and placed here.
   - New (untracked) files must be added to the staging area before git will track them.
   - If a tracked file has been changed it must be added to staging area for that change to be included in a commit.
   - This is known as staging files or adding them to the staging area.
   - Only files in the staging area are included in a commit.

- The Repository
   - When you run git commit a new commit is created in the repository.
   - All files in the staging area are moved to the repository as part of the new commit.

  

Key Points covered:

- **git status** shows the status of a repository.
- Files can be stored in a project’s working directory (which users see), the staging area (where the next commit is being built up) and the local repository (where commits are permanently recorded).
- **git add** puts files in the staging area.
- **git commit** saves the staged content as a new commit in the local repository.
- **git log** displays history of changes and all the commits information
Write a commit message that accurately describes your changes.

![Commands_flow](./fig/Commands_flow.png)
