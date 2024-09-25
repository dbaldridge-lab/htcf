
## What is the use of the .bashrc file?

Bash is a shell, a command processor that typically runs in a text window where the user types commands that cause actions.

The .bashrc file is a configuration file that is executed whenever a new terminal session is started in **interactive mode**. This file contains commands to set up the shell for use in your particular environment. 

You can use it to save time and typing by:
- setting environment variables (e.g. editing the prompt and PATH)
- sourcing helper files (e.g. making spack commands work without eval())
- defining aliases - give a shortened name to a command you enter frequently
- defining functions - name a sequence of commands that you will reuse and that may take input. (NOTE: This is specific to your user profile. Others won't be able to use or see code here.)

On HTCF, .bashrc is sourced by your login shell and the shells you enter after running srun or salloc commands. 

This file will not be sourced for batch jobs submitted to SLURM using ```sbatch yourjobscript.sh```. 

## suggested .bashrc additions
1. Copy what you find useful from the code block below
2. open a terminal and connect to HTCF using ssh (review [these instructions](https://github.com/dbaldridge-lab/htcf/blob/main/htcf_access.md))
3. open the .bashrc file by typing ```nano ~/.bashrc``` and pressing `enter`
4. press the down arrow key until your cursor is at the end of the file
5. Press `cmd+v` to add the text to the bottom of your file
6. Press `ctrl+x` to exit, type `y` to save.
7. To see changes reflected, type ```source ~/.bashrc``` at the prompt and press `enter`

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
alias sml='srun --mem=5G --cpus-per-task=1 -J interactive -p interactive --pty /bin/bash -l' #use this most of the time
alias med='srun --mem=20G --cpus-per-task=1 -J interactive -p interactive --pty /bin/bash -l'
alias lrg='srun --mem=100G --cpus-per-task=1 -J interactive -p interactive --pty /bin/bash -l'

# lab vscode software location
alias code='/ref/dblab/software/vscode/code'

# Safe versions of the default commands. Will ask permission before overwriting files.
alias rm='rm -i'
alias mv='mv -i'
alias cp='cp -i'
###################################################################################
```
