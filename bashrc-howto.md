
## What is the use of the .bashrc file?

Bash is a shell, a command processor that typically runs in a text window where the user types commands that cause actions.

The .bashrc file is a configuration file that is executed whenever a new terminal session is started in **interactive mode**. This file contains commands to set up the shell for use in your particular environment. 

You can use it to save time and typing by:
- setting environment variables (e.g. editing the prompt and PATH)
- defining aliases - give a shortened name to a command you enter frequently
- defining functions - a sequence of commands that you will reuse that can take input. (NOTE: If a function is part of a standard analysis, then it doesn't belong here, as this is specific to your user profile.)

On HTCF, .bashrc is sourced by your login shell and the shells you enter after running srun or salloc commands. You can manually source this file by typing ```source ~/.bashrc``` at the prompt, which you will want to do after you make changes.

This file will not be ran for batch jobs submitted to SLURM. It will also not be ran when opening the Terminal app on MacOS, where the default shell is zsh. You are welcome to use any shell of your choice, but setup and troubleshooting of custom configurations are left up to the user.

