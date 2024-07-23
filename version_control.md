If you're new to version control and wondering why this is important, 
[this is a nice overview](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1004668).

## Initial git setup
1. Open a terminal
2. Check if you have git installed on your local machine with `git --version`
  - If you receive an error, [download git](https://git-scm.com/downloads) 
3. configure git so it knows who is making changes
  - Set your username: `git config --global user.name "FIRST_NAME LAST_NAME"`
  - Set your email address: `git config --global user.email "my_wustl_key@wustl.edu"`
    
## Version control your code with git

1. Read the [documentation](https://git-scm.com/docs) or find a tutorial and learn how to use the following commands:
```
git init 
git status
git add
git commit
```
2. Create a [.gitignore file](https://docs.github.com/en/get-started/getting-started-with-git/ignoring-files)
that lists files, filetypes, and directories that don't want version controlled in your project:
- raw data
- figures
- code output
- excel files(use .csv)
- word documents(use .md)
  
***Best practice is to not place those files in a version controlled directory to begin with,
and only use .gitignore to catch exceptions.***

3. Add version control to an existing project or create a new project. ***Use one repository per project.***
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
    - Expiration is optional, I typically set it to one year from creation date
  - You will be prompted for your username and password when you try to push, pull, or clone a repository.
    - Use your GitHub username as the username, and your personal access token as the password.

If you want to avoid entering your PAT every time you push, you can store your credentials by entering the following command: 

`git config --global credential.helper store`

## Sharing code on GitHub
1. Read the [documentation](https://git-scm.com/docs) or find a tutorial to understand what each of the commands below does.
```
git push  # push your changes to GitHub
git clone  # grab all code for a repo from GitHub
git pull  # grab most recent changes
```
2. Connect local version controlled files with a remote repository on GitHub.
[How-to](https://docs.github.com/en/get-started/getting-started-with-git/managing-remote-repositories)
3. Fetch from the remote GitHub main branch (origin) to your local main branch (main) to keep your local copy up to date.
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
