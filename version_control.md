If you're new to version control and wondering why this is important, 
[this is a nice overview](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1004668).

## Initial git setup
Complete the following setup on both your local machine and HTCF:

1. Open a terminal
2. Check if git is installed by typing `git --version` at the prompt.
    - If you receive an error, [download git](https://git-scm.com/downloads) 
3. Configure git so it it is clear who is making changes
Set your username. Change only the FIRST_NAME and LAST_NAME fields in the following command:
```
git config --global user.name "FIRST_NAME LAST_NAME"
```
Set your email address:
```
git config --global user.email "my_wustl_key@wustl.edu"
```
Confirm your changes
```
git config --global --list
```

## Which files should I track using version control?

Code and relevant flat files (.txt, .csv, etc.) should be added to git repositories and synced with GitHub.

### Do not track data files
- Move raw and processed data files to RIS using Globus. 
- Once all data processing is completed, consider deleting large intermediate files that can be re-generated.
- Retain all log files, preferably in the same folder as the finalized results on RIS.

### Store Jupyter Notebooks with output in Lab Archives... 
Notebooks can be stored alongside other experimental documentation on Lab Archives. 
Save the file after executing the code blocks so the results can be previewed.

### ... but also version control a copy of the notebook source code
Code in Jupyter notebooks can be converted to a format more compatible with version control tools using Jupytext. 

Jupytext will generate an equivalent .py file synced with changes to a paired notebook:
```
# Activate an environment with Jupytext installed
spack env activate -p jupyter

# Create a copy of the notebook file converted to .py
jupytext --to py example.ipynb

# Pair the files
jupytext --set-formats ipynb,py:percent example.ipynb

# Sync the files
jupytext --sync example.py
```

## Setting up a new repository using VSCode
***Use one repository per project.***
1. Connect a local repository (e.g. on HTCF or local machine) to a remote repository on GitHub:
This is one of many approaches:
- Create a new repository on GitHub
![image](https://github.com/user-attachments/assets/c3717bd2-1ce8-45de-a099-bfb4065bbabe)
![image](https://github.com/user-attachments/assets/8bbb2eee-5611-4ed8-9906-36196552882a)
- grab the URL
- Open the GitHub Pull Requests tab in VSCode:
![image](https://github.com/user-attachments/assets/262dc9c6-3b57-4a54-96ff-239f6165fd35)
- Select `Configure remotes...`
- Click `Add Item`
- paste the URL

[Here's another approach.](https://docs.ris.wustl.edu/doc/compute/workshops/ris-software-development.html#creating-a-repository) 

2. Create a [.gitignore file](https://docs.github.com/en/get-started/getting-started-with-git/ignoring-files) that lists filetypes and directories that you don't want version controlled:
- raw data
- figures
- code output
- excel files (use .csv)
- word documents (use .md or .txt)

## Getting comfortable with git

1. Read the [documentation](https://git-scm.com/docs) or find a tutorial and learn how to use the following commands:
```
git init 
git status
git add
git commit
```
2. 

3. Add version control to an existing project or create a new project. 
4. Make changes and test making commits. ***Make descriptive commit messages (AI can help).***

## Initial GitHub setup
1. Create a GitHub account or add your wustl email to an existing account
2. An admin of the group or RIS will add this account to dbaldridge-lab
3. Create a Personal Access Token (PAT)
  - Go to your GitHub settings (click on your profile picture in the top right corner and select "Settings").
  - In the left sidebar, click on "Developer settings". ![image](https://github.com/dbaldridge-lab/htcf/assets/50468813/c4a32562-6686-4ed2-b8f4-47fe5d233ead)

  - In the left sidebar, click on "Personal access tokens". ![image](https://github.com/dbaldridge-lab/htcf/assets/50468813/1eecf8e5-7d13-4e01-86b7-68353c1b17ec)

  - Click on "Generate new token (classic)". ![image](https://github.com/dbaldridge-lab/htcf/assets/50468813/0f57ad98-b16b-4884-a07c-416c15edae2c)

  - Give your token a descriptive name, select the scopes (or permissions) you want to grant this token, and click on "Generate token".
    - ***Be sure to copy your new personal access token now. You won’t be able to see it again!***
    - Never share your access token, it is a password
    - In VSCode, select 
    - ![image](https://github.com/user-attachments/assets/226d781d-604e-409f-8f36-1d9b0cb55b9d)

  - You will be prompted for your username and password when you try to push, pull, or clone a repository.
    - Use your GitHub username as the username, and your personal access token as the password.

If you want to avoid entering your PAT every time you push, you can store your credentials by entering the following command: 

`git config --global credential.helper store`

## Sharing code on GitHub
1. Read the [documentation](https://git-scm.com/docs) or find a tutorial to understand what each of the commands below does.
```
git push  # (local -> remote) puts your changes on GitHub
git clone  # copy all code for a repo from GitHub
git pull  # (remote -> local) grabs most recent changes from GitHub
```
2. Connect local version controlled files with a remote repository on GitHub.
[How-to](https://docs.github.com/en/get-started/getting-started-with-git/managing-remote-repositories)
3. Pull changes from the remote GitHub main branch (origin) to your local main branch (main) to keep your local copy of the codebase up to date.
4. Make changes on main and push them up to origin. ***If multiple people are making edits, repeat this and the previous step frequently.***

## IDEs and git clients can help
[RStudio](https://happygitwithr.com/usage-intro)

[VSCode](https://code.visualstudio.com/docs/sourcecontrol/intro-to-git#_open-a-git-repository)

## Git on HTCF
Git comes pre-installed on HTCF.

<img width="137" alt="image" src="https://github.com/dbaldridge-lab/htcf/assets/50468813/969da79e-01e9-4c68-a9aa-29397c1e4c97">

For the purposes of this tutorial, think of HTCF as a secondary local machine you use.

## Undoing changes
[How to undo almost anything with git](https://github.blog/2015-06-08-how-to-undo-almost-anything-with-git/)
```
git revert
git commit --amend
git rm
```

## Git Workflow
Workflow is up to the discretion of the project owner. For small teams, a [centralized workflow](https://anything-git.readthedocs.io/en/latest/git_workflow.html) is usually sufficient. 

A more complicated workflow utilizing feature branches can be useful in cases where:
- several people are making changes to the code
- the project lead wants to review code before it gets added to the main branch
- changes to multiple features, figures, or improvements are in-progress and changes will occur over a number of weeks
  - [Using branches](https://www.atlassian.com/git/tutorials/using-branches)
- the team plans to use pull requests to get feedback or facilitate troubleshooting
  - [Making pull requests on Github](https://docs.github.com/en/get-started/start-your-journey/hello-world)
  
```
git branch
git checkout
git merge
```
### TO DO
- [ ] add .gitignore project template
- [ ] Test if two people can push from same repo on HTCF. Will same credentials show for both?
    - [ ] Starting a new shared repo on HTCF ![image](https://github.com/user-attachments/assets/5d86ef56-9f36-4c9c-b6e7-5fd6184499ed)
