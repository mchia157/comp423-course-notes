# Setting up a dev container for Go

* Primary author: [Pilar Chia](https://github.com/mchia157)
* Reviewer: [Anya Vourakis](https://github.com/v-anya)

## Introduction
Welcome everyone! In this tutorial, you'll learn how to set up a dev container with the Go programming language in Visual Studio Code. Let's have some fun!

## Prerequisites 
To start with this tutorial, you'll need to set up (if you haven't yet) the following:

1. **Your GitHub account**: [Log In or Sign Up](https://github.com/)
2. **Git**: Run `git --version` in your terminal to confirm if you have it or [download](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
3. **Visual Studio Code**: [Download here](https://code.visualstudio.com/)
4. **Docker**: [Download here](https://www.docker.com/products/docker-desktop/)

!!! Warning 
    Do not move forward unless all these are downloaded and installed. 

## Step-by-Step Guide

### Part 1. Creating the Repository
#### Step 1. Create a Local Directory and Initialize Git

(1) Open your terminal or command prompt.

(2) Create a new directory for your project. 
!!! note

    If you'd like to organize this tutorial somewhere else on your machine, go ahead and change into that parent directory first.

    
```bash
mkdir go-setup-project
cd go-setup-project
```

(3) Initialize a new Git repository:

`git init`

(4) Create a README file:

```bash
echo "# Go Set Up Project from https://mchia157.github.io/comp423-course-notes/tutorials/go-setup/" > README.md
git add README.md
git commit -m "Initial commit with README"
```
#### Step 2. Create a Remote Repository on GitHub
(1) Log in to your GitHub account and navigate to the [Create a New Repository](https://github.com/new) page.

(2) Fill in the details as follows:

* __Repository Name__: `go-setup-project`
* __Description__: "Tutorial to set up dev containers using Go programming language."
* __Visibility__: Public

(3) Do not initialize the repository with a README, .gitignore, or license.

(4) Click **Create Repository**.
#### Step 3. Link your Local Repository to GitHub
(1) Add the GitHub repository as a remote:

```bash
git remote add origin https://github.com/<your-username>/go-setup-project.git
```
!!! Warning
    Make sure to replace `<your-username>` with your GitHub username.

(2) Check your default branch name with the subcommand `git branch`. If it's not `main`, rename it to `main` with the following command:
```bash
git branch -M main
```
!!! Note
    Old versions of git choose the name master for the primary branch, but these days main is the standard primary branch name.

(3) Push your local commits to the GitHub repository:

`git push --set-upstream origin main`

(4) Back in your web browser, refresh your GitHub repository to see that the same commit you made locally has now been pushed to remote. You can use git log locally to see the commit ID and message which should match the ID of the most recent commit on GitHub. This is the result of pushing your changes to your remote repository.
