If you're new to version control and wondering why this is important, 
[this is a nice overview](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1004668).

## Initial GitHub setup
1. Create a GitHub account or add your wustl email to an existing account
2. An admin of the group or RIS will add this account to dbaldridge-lab

## Initial git setup
1. Open a terminal
2. Check if git is installed by typing `git --version` at the prompt.
    - If you receive an error, [download git](https://git-scm.com/downloads)
    - git is already installed on HTCF
3. Configure git so it it is clear who is making changes. Repeat this step for each machine you plan to work on (HTCF, laptop, etc.):
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
Activate an environment with Jupytext installed
```
spack env activate -p jupyter
```
Create a copy of the notebook file converted to .py
```
jupytext --to py example.ipynb
```
Pair the files
```
jupytext --set-formats ipynb,py:percent example.ipynb
```
Sync the files
```
jupytext --sync example.py
```

## Setting up a new repository
***Use one repository per project.***
1. Connect a local repository (e.g. on HTCF or local machine) to a remote repository on GitHub.
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

[And another.](https://docs.github.com/en/get-started/getting-started-with-git/managing-remote-repositories)

2. Create a [.gitignore file](https://docs.github.com/en/get-started/getting-started-with-git/ignoring-files) that lists filetypes and directories that you don't want version controlled:

    - At the head directory of a new repository, add this [.gitignore template](https://github.com/dbaldridge-lab/htcf/blob/main/.gitignore), editing as needed.

## Getting comfortable with git and GitHub

1. Read the [documentation](https://git-scm.com/docs) or find a tutorial and learn how to use the following commands to version control code in a local branch:
```
git init 
git status
git add
git commit
```
2. Commit frequently. Summarize the changes made with a short, descriptive message.
3. Learn how to sync changes mode locally with a remote branch:
```
git push  # (local -> remote) puts your changes on GitHub
git clone  # copy all code for a repo from GitHub
git pull  # (remote -> local) grabs most recent changes from GitHub
```
- Pull changes from the remote GitHub main branch (origin) to your local main branch (main) to keep your local copy of the codebase up to date.
- Make changes on main and push them up to origin. ***If multiple people are making edits, repeat this and the previous step frequently.***
4. Undoing changes
[How to undo almost anything with git](https://github.blog/2015-06-08-how-to-undo-almost-anything-with-git/)
```
git revert
git commit --amend
git rm
```

## IDEs and git clients can help
[RStudio](https://happygitwithr.com/usage-intro)

[VSCode](https://code.visualstudio.com/docs/sourcecontrol/intro-to-git#_open-a-git-repository)
Note: When using the source control tab and tunneling to VSCode on HTCF:
1. Connect to HTCF using SSH in the first window
2. Split the terminal in this window
   - first terminal: start interactive session and start tunnel
   - second terminal: no actions required, but will keep VSCode from disrupting the tunnel
4. open the folder with a git repo
5. Commit and push from this window

## Suggested Git Workflow
A [centralized workflow](https://anything-git.readthedocs.io/en/latest/git_workflow.html) is usually sufficient. 

A more complicated workflow utilizing feature branches can be useful in cases where:
- several people are making changes simultaneously
- code is reviewed before being added to the main branch
- multiple independent updates are in-progress and changes will occur over a number of weeks
  - [Using branches](https://www.atlassian.com/git/tutorials/using-branches)
- the team plans to use pull requests to get feedback or facilitate troubleshooting
  - [Making pull requests on Github](https://docs.github.com/en/get-started/start-your-journey/hello-world)
```
git branch
git checkout
git merge
```
### TO DO
- [ ] Test if two people can push from same repo on HTCF. Will same credentials show for both?
