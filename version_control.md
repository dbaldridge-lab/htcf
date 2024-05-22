git and GitHub can be daunting at first, but a few commands are all you need to get started. 

Sections below are listed in order of importance; 
get comfortable with the information under one heading before moving on to the next. 

If you're new to version control and wondering why this is important, 
[this is a nice overview](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1004668).

## Version control your code with git
1. Start by [downloading git](https://git-scm.com/downloads) on your local machine.
2. Open a terminal
3. Set your username: `git config --global user.name "FIRST_NAME LAST_NAME"`
4. Set your email address: `git config --global user.email "my_wustl_key@wustl.edu"`
5. Read [documentation](https://git-scm.com/docs) or find a tutorial to understand the following commands.
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


[]


1. Test creating a new branch locally in an existing project using the command line or your preferred IDE.
2. Test checking out and making changes on the local branch, pushing those changes to GitHub, and merging those in to the main branch on GitHub.

## Undoing changes
[How to undo almost anything with git](https://github.blog/2015-06-08-how-to-undo-almost-anything-with-git/)
```
git revert
git commit --amend
git rm
```

## Git Branch
Use of branches is completely optional, but can be useful:
- when there are multiple people making code changes
- if you are juggling changes to multiple features, figures, or improvements
  
[Using branches](https://www.atlassian.com/git/tutorials/using-branches)
```
git branch
git checkout
git merge
```
[Making pull requests on GitHub](https://docs.github.com/en/get-started/start-your-journey/hello-world)
