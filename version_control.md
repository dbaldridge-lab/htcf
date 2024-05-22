git and GitHub can be daunting at first, but a few commands are all you need to get started. 

Sections are listed in order of importance; get comfortable with the information under one heading before moving on to the next. 

If you're new to version control and wondering why this is important, [this is a nice overview](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1004668).

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
6. Add version control to an existing project or create a new project.
7. Make changes and test making commits.

## Sharing code on GitHub
1. Create a GitHub account or add your wustl email to an existing account
2. admin will add this account to dbaldridge-lab
3. Read [documentation](https://git-scm.com/docs) or find a tutorial to understand what each of the commands below does.
```
git push
git clone
git pull
```
4. Connect local version controlled files with a remote repository on GitHub. [How-to](https://docs.github.com/en/get-started/getting-started-with-git/managing-remote-repositories)
5. Make changes and make a pull request.
6. Review code and accept a pull request.

## Collaborating on a repo OR you have multiple in-progress features/figures/improvements
[Managing branches using GitHub interface](https://docs.github.com/en/get-started/start-your-journey/hello-world)
```
git branch
git checkout
git merge
```
1. Test creating a new branch locally in an existing project using the command line or your preferred IDE.
2. Test checking out and making changes on the local branch, pushing those changes to GitHub, and merging those in to the main branch on GitHub.

## What did the code look like on a certain date
```
git revert
```


