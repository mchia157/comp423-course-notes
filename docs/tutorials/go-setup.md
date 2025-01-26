# Setting up a dev container for Go

* Primary author: [Pilar Chia](https://github.com/mchia157)
* Reviewer: [Anya Vourakis](https://github.com/v-anya)

## Introduction
Welcome everyone! In this tutorial, you'll learn how to set up a development contaniner (dev container) for the Go programming language in Visual Studio Code (VS Code). Let's have some fun!

## Prerequisites 
To start with this tutorial, you'll need to set up (if you haven't yet) the following:

1. **Your GitHub account**: [Log In](https://github.com/login) or [Sign Up](https://github.com/signup?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F&source=header-home)
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

```bash
git push --set-upstream origin main
```

(4) Back in your web browser, refresh your GitHub repository to see that the same commit you made locally has now been pushed to remote. You can use git log locally to see the commit ID and message which should match the ID of the most recent commit on GitHub. This is the result of pushing your changes to your remote repository.

### Part 2. Setting Up the Development Environment
#### Step 1. Add Development Container Configuration

1. In VS Code, open the `go-setup-project` directory. You can do this via: File > Open Folder.
2. Install the [Dev Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) for VS Code.
3. Create a .devcontainer directory in the root of your project with the following file inside of this "hidden" configuration directory:
`.devcontainer/devcontainer.json`

The `devcontainer.json` file defines the configuration for your development environment. Here, we're specifying the following:

* **`name`**: A descriptive name for your dev container.
* **`image`**: The Docker image to use, in this case, the latest version of a Go environment. Microsoft maintains a collection of base images for many programming language environments, but you can also create your own!
* **`features`**: Ensures Go is installed and up-to-date.
* **`customizations`**: Installs the official Go plugin by the Go Team at Google.
```json title=".devcontainer/devcontainer.json"
{
  "name": "Go Set Up Project",
  "image": "mcr.microsoft.com/devcontainers/go:latest",
  "features": {
    "ghcr.io/devcontainers/features/go:1": {
      "version": "latest"
    }
  },
  "customizations": {
    "vscode": {
      "extensions": [
        "golang.go"
      ]
    }
  }
}
```
#### Step 2. Reopen the Project in a VSCode Dev Container
Reopen the project in the container by pressing `Ctrl+Shift+P` (or `Cmd+Shift+P` on Mac), typing "Dev Containers: Reopen in Container," and selecting the option. This may take a few minutes while the image is downloaded and the requirements are installed.

Once your dev container setup completes, close the current terminal tab (trash can), open a new terminal pane within VSCode, and try running `go version` to see your dev container is running a recent version of Go.

### Part 3. Creating a new Go project
#### Step 1. Initialize a Go module

```bash
go mod init hello-world
```

#### Step 2. Create a new Go file 
By convention, you'll call the file `main.go`

``` go title="main.go"
package main

import "fmt"

func main(){
  fmt.Println("Hello COMP423")
}
```

#### Step 4. Run the program 

``` bash
go run main.go
```

!!! Note
    The subcommand run compiles and runs the code in one step, but does not create a standalone executable.

#### Step 4. Create an executable file named `hello-world`

``` bash
go build -o hello-world main.go
```
!!! info
    `-o hello-world` indicates the excecutable is written to the hello-world output file.

!!! Note
    The subcommand build compiles the code and generates a standalone executable, so the program can be run without installing go.

#### Step 5. Add, commit, and push your work

Write the following on your terminal:

``` bash
git add .
git commit -m "Created my first Go project"
git push origin main
```

## Conclusion
Congratulations! You've successfully created a dev container using VS Code for Go development and completed your first project.
