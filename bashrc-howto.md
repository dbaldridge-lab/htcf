
## What is the use of the .bashrc file?

Bash is a shell, a command processor that typically runs in a text window where the user types commands that cause actions.

The .bashrc file is a configuration file that is executed whenever a new terminal session is started in **interactive mode**. This file contains commands to set up the shell for use in your particular environment. You can use it to set environment variables, define aliases, and define functions.

On HTCF this is executed for your login shell and the shells you enter after running srun or salloc commands. 

This file will not be ran for batch jobs submitted to SLURM. It will also not be ran when opening the Terminal app on MacOS, where the default shell is zsh.

