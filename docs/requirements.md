---
layout: default
title: Requirements
nav_order: 2
---

# Requirements and setup for this project
As we want to give all users the chance to 
run code as part of their team, we need to make
sure that the _development environment_ on each
user's machine is roughly the same. Please 
ensure that prior to the event the following has
been completed:
* Ensure you have access to ADNI data. If you do not already have access to the ADNI data set, please visit their [Accessing data](https://adni.loni.usc.edu/data-samples/access-data/) section to find out how to obtain access.
* Make sure that a recent version of Python (either using [Anaconda](https://www.anaconda.com/products/distribution) or [Miniconda](https://docs.conda.io/en/latest/miniconda.html)) is installed. We will use this to create a working environment that will install all the required packages and ensure that this project is kept separate from your regular work.

## Setting up a conda environment
Nowadays you will run into various data science Python packages that may require specific dependencies that will result in clashes with other packages that you want to work with, particularly if you want to be able to reproduce various analyses you have done. 

For example, you may be working on "project A" that has code that needs the specific versions of the following packages:
* Numpy version 1.21.0, 
* matplotlib version 3.5.0,  
* pandas version 1.4.3. 
 
You may then start "project B", where you receive software from a new group that requires updated versions of all three of those packages. 

Virtual environments allow you to creat a new directory that holds separate versions of all of these packages that don't interfere with each other. You can switch from one enviornment to another depending on what you are working on. For the purpose of this workshop, we will be creating a new environment on your laptops (assuming you have anaconda/miniconda installed as mentioned above). 

To do that, you will need to download the code from Github or the Microsoft Teams site. Then, on the command line, you will need to go to the directory where you downloaded the code and type in the following command:
```
conda env create -f environment.yml
```
This will install the enviroment that is specified in the file called `environment.yml`. That file tells anaconda to create an environemnt called teamcoder_ebm with all of the packages that you will need to complete the tasks. 

## Optional: Collaborating with Github
One way to work as a team is to use Github to sync code between team members. If your team is interested in this, then the additional requirements are needed.
* Create a [github](https://github.com) account.
* Ensure that [git is installed](https://github.com/git-guides/install-git) locally on the machine you are planning to use.
* Consider installing [GitHub Desktop](https://desktop.github.com/), a simple graphical interface for working with projects in git. If you don't have git installed already, GitHub Desktop should do that step for you.
