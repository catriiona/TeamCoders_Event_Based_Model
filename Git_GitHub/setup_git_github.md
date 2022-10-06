### Set up a GitHub account

If you do not have one, sign up for a GitHub account at [github.com](https://github.com/).

### Create a repository

learn how to create a repository
[Create a repo](https://docs.github.com/en/free-pro-team@latest/articles/create-a-repo) with name 

# Work with Git

- This document introduces some basic usage of [Git](https://git-scm.com/), a distributed versioning system for tracking and managing source code changes during software development.

- [IDEAS](https://github.com/HealthBioscienceIDEAS/TeamCoders_Event_Based_Model) and [GitHub](https://github.com/) are two project hosting services. The [TeamCoders_Event_Based_Model repository](https://github.com/HealthBioscienceIDEAS/TeamCoders_Event_Based_Model) is hosted on the former, while you will submit your work to your GitHub Team repository.
- For more information and tutorial, have a look at the book/documentation [*Pro Git*](https://git-scm.com/book/en/v2)

- [IDEAS](http:///) and [GitHub](https://github.com/) are two project hosting services. The [TeamCoders_Event_Based_Model repository](https://github.com/HealthBioscienceIDEAS/TeamCoders_Event_Based_Model) is hosted on the former, while you will submit your coursework to the latter.
- For more information and tutorial, have a look at the book/documentation [*Pro Git*](https://git-scm.com/book/en/v2)


# Start with Git

When we use Git on a new computer for the first time, we need to configure a few things. You must provide some extra information before it is ready to interact with Git. Below are a few examples of configurations we will set as we get started with Git:

- our name and email address,
- what our preferred text editor is,
- and that we want to use these settings globally (i.e. for every project).

This configuration gives the identity of the user in any project which you might work on your computer. In collaborative projects this is used to distinguish who has made what changes. You only need to perform the above commands once for each new computer Git is installed on.

```bash
 git config --global user.name "FIRST_NAME LAST_NAME"   # Use the name that you wish to be identified 

 git config --global user.email "email@example.com"  # Use your email that is linked with your GitHub 
 ```
```bash
 git config --global core.editor "nano-w"   # Use the nano editor as main editor- you can use others like atom as  "atom --wait" or Vim as 'vim' or VS Code as "code --wait" 
 ```
 
 ```bash
 git config --global init.defaultBranch main   # call the default branch as main to be consistent with GitHub 
 ```
 If you want to check your configurations type git config --list
  
 ```bash
 git config --list  # shows all your configurations
 ```


## Team editor FORKs the TeamCoders repostory from the  GitHub of IDEAS
Find your Team and decide who is going to be the team 'editor'. Only the Team Editor FORKS from IDEAS



## Clone the TEAMCODERS repository from your TEAM EDITOR repository to your local machine

Lets say that your editor is called Ed and his GitHub is ed-somone then the repository is most likely to be
https://https://github.com/ed-someone/HealthBioscienceIDEAS/TeamCoders_Event_Based_Model
Make a local copy of the entire repository hosted on the remote IDEAS site, e.g. remote repository -> local repository.

``` bash
git clone https://https://github.com/ed-someone/HealthBioscienceIDEAS/TeamCoders_Event_Based_Model
```
**Do not use the above path** Your team editor, will give you the correct path
Change the current directory to the repository folder, then update to the latest code.

``` bash
cd # TeamCoders_Event_Base_Model
git pull
```

## Complete the challenge work  and updatethe repository on the GitHub


### Record you progress

Git supports complex workflows for large professional software development projects. A (over-)simplified single-user project may only need a few steps/commands.

- Make changes to your code on your local repository.
- Add the changes (or new files) to Git, so they become tracked.
- Commit these changes with a commit message.
- Push the commits to the remote repository.

```bash
git add file_you_wish_to _change_from_your_local_directory
git commit -m "a brief message summarise the committed changes"
git push origin main
```

In this workshop we wil learn very basic operations with Git. The team editor will make changes on her/his local repository (computer), save them, committ the changes, then push them to her/his GitHub. Then the team members will pull and update the repository in their mashines

If you wish to learn more about collaborating coding, the workflow is likely to be more complex and [branching and merging](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging) will become handy.
