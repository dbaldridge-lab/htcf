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

*Do not track large data files. These belong in long term storage.*

### Store Jupyter Notebooks with output in Lab Archives... 
It can be convenient to store notebooks alongside other experimental documentation on Lab Archives. 
Save the file after executing the code blocks. Add as an attachment to a Lab Archives page so the results can be previewed and the code can be downloaded as needed.

### ... but also version control a general copy of the notebook source code
Clear outputs and save prior to commiting.

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

1. Read the [documentation](https://git-scm.com/docs) or find a tutorial and learn how to use the following commands to version control code in a git repository:
```
git init 
git status
git add
git commit
```
2. Commit frequently. Summarize the changes made with a short, descriptive message.
3. Learn how to sync changes made locally with a remote repository:
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

[VSCode](https://code.visualstudio.com/docs/sourcecontrol/intro-to-git#_staging-and-committing-code-changes)

Note: When using the source control GUI and tunneling to VSCode on HTCF:
1. Connect to HTCF using SSH in the first window
2. Open the folder containing a git repo
3. Connect to the tunnel in a second window
5. Edit files in the second window and commit and push from the first window

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
