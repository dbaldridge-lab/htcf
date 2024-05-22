git and GitHub can be daunting, but a few commands and a bit of setup are all you need to get started. 

Sections below are listed in order of importance; 
get comfortable with the information under one heading before moving on to the next. 

If you're new to version control and wondering why this is important, 
[this is a nice overview](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1004668).

## Version control your code with git
1. Start by [downloading git](https://git-scm.com/downloads) on your local machine.
2. Open a terminal
3. Set your username: `git config --global user.name "FIRST_NAME LAST_NAME"`
4. Set your email address: `git config --global user.email "my_wustl_key@wustl.edu"`
5. Read [documentation](https://git-scm.com/docs) or find a tutorial and learn how to use the following commands:
```
git init
git status
git add
git commit
```
6. Create a [.gitignore file](https://docs.github.com/en/get-started/getting-started-with-git/ignoring-files)
that lists files, filetypes, and directories that don't want version controlled in your project:
- raw data
- figures
- code output
- excel files(use .csv)
- word documents(use .md)
  
***Best practice is to not place those files in a version controlled directory to begin with,
and only use .gitignore to catch exceptions.***

7. Add version control to an existing project or create a new project. ***Use one repository per project.***
8. Make changes and test making commits. ***Make descriptive commit messages (AI can help).***

## Sharing code on GitHub
1. Create a GitHub account or add your wustl email to an existing account
2. admin will add this account to dbaldridge-lab
3. Read [documentation](https://git-scm.com/docs) or find a tutorial to understand what each of the commands below does.
```
git push
git clone
git pull
```
4. Connect local version controlled files with a remote repository on GitHub.
[How-to](https://docs.github.com/en/get-started/getting-started-with-git/managing-remote-repositories)
6. Make changes and make a pull request.
7. Review changes and accept a pull request.

## IDEs and git clients can help
[RStudio](https://happygitwithr.com/usage-intro)

[VSCode](https://code.visualstudio.com/docs/sourcecontrol/intro-to-git#_open-a-git-repository)

## Git on HTCF

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
- many people are making changes to the code
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
