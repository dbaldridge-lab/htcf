
## What is the use of the .bashrc file?

Bash is a shell, a command processor that typically runs in a text window where the user types commands that cause actions.

The .bashrc file is a configuration file that is executed whenever a new terminal session is started in **interactive mode**. This file contains commands to set up the shell for use in your particular environment. 

You can use it to save time and typing by:
- setting environment variables (e.g. editing the prompt and PATH)
- defining aliases - give a shortened name to a command you enter frequently
- defining functions - name a sequence of commands that you will reuse and that may take input. (NOTE: If a function is part of a standard analysis, then it doesn't belong here, as this is specific to your user profile.)

On HTCF, .bashrc is sourced by your login shell and the shells you enter after running srun or salloc commands. 

This file will not be sourced for batch jobs submitted to SLURM using ```sbatch yourjobscript.sh```. 

If working locally, note that this file will also not be sourced when opening the Terminal app on MacOS, where the default shell is zsh.

You are welcome to use any shell of your choice, however setup and troubleshooting of custom configurations are left up to the user.

## suggested .bashrc additions
1. Copy what you find useful from the ### quoted text ### on this page by highlighting and pressing cmd+C
2. open a terminal and connect to HTCF using ssh (review [these instructions](https://github.com/dbaldridge-lab/htcf/blob/main/htcf_access.md))
3. open the .bashrc file by typing ```nano ~/.bashrc``` and pressing enter
4. press the down arrow key until your cursor is at the end of the file
5. Press cmd+v to add the text to the bottom of your file
6. Press ctrl+x to exit, type y to save.
7. To see changes reflected, manually source this file by typing ```source ~/.bashrc``` at the prompt and pressing enter, or close out of your terminal and log back in.

```
##################################################################################
# Leave back to back duplicates and commands with leading whitespace out of history
export HISTCONTROL=ignorespace:ignoredups

# spack bash helper setup
. /ref/dblab/software/spack-0.21.0/share/spack/setup-env.sh

# Navigating the HTCF file system
alias scratch="cd /scratch/dblab"
alias lts="cd /lts/dblab"
alias ref="cd /ref/dblab/software"

# Navigate to higher level directories quickly
alias ..="cd .."
alias ...="cd ../.."

# Interactive sessions. Larger sizes have more memory per node.
alias js='srun --mem=1G --cpus-per-task=1 -J interactive -p interactive --pty /bin/bash -l' #just a shell
alias sml='srun --mem=2G --cpus-per-task=1 -J interactive -p interactive --pty /bin/bash -l' #use this most of the time
alias med='srun --mem=8G --cpus-per-task=1 -J interactive -p interactive --pty /bin/bash -l'
alias lrg='srun --mem=20G --cpus-per-task=1 -J interactive -p interactive --pty /bin/bash -l'

# lab vscode server location
alias code='/ref/dblab/software/vscode/code'

# Safe versions of the default commands. Will ask permission before overwriting files.
alias rm='rm -i'
alias mv='mv -i'
alias cp='cp -i'

# Makes the prompt more user-friendly.
export PS1='\[\e]0;\w\a\]\n\[\e[32m\]\u@\h \[\e[33m\]\w\[\e[0m\]\n\$ '

# This is required for Entrez Direct to work. Disables strict checking of an encryption page.
export PERL_LWP_SSL_VERIFY_HOSTNAME=0
###################################################################################
```
