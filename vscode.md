# Setting up VSCode
[Skip to normal setup process](https://github.com/dbaldridge-lab/htcf/blob/main/jupyter_vscode.md#normal-process)

## Prerequisites
- [Visual Studio Code](https://code.visualstudio.com/) is installed on your local machine
- WUSTL microsoft account login information
- Updated ~/.bashrc file on HTCF to include "code" alias. [See instructions here.](https://github.com/dbaldridge-lab/htcf/blob/main/bashrc-howto.md)

## Do this once
### 1. Setup code command

a. On your local machine, open Visual Studio Code.

b. Press CMD + SHIFT + P to open the Command Palette.

c. Type shell command to find the `Shell Command: Install 'code' command in PATH` command.

d. After executing the command, restart the terminal for the new $PATH value to take effect. 

e. verify setup by typing `code --version` in your terminal. 
If it prints out the version of Visual Studio Code, proceed.

Now when you are using a terminal, you can simply type `code .` to start editing files in the current folder.
You can also add an option -r and provide the path to a file. This will open the file in a new tab in the current window: `code -r <filename>`.

### 2. Install Extensions 
- Open VSCode on your local machine
- Go to Extensions <img width="33" alt="image" src="https://github.com/dbaldridge-lab/htcf/assets/50468813/7b07ab0f-e68f-4b33-954b-2ac556c2ddb9">
(Shortcut: `Cmd+Shift+X`)
- Search and install the following extensions:
    - `ms-vscode-remote.remote-ssh`
    - `ms-vscode-remote.remote-ssh-edit`
    - `ms-vscode.remote-server`
    - `ms-vscode.remote-explorer`
    - `ms-vscode.remote-repositories`
    - `ms-python.python`
    - `ms-toolsai.jupyter`
    - `ms-toolsai.vscode-jupyter-cell-tags`
    - `ms-toolsai.jupyter-keymap`
    - `ms-toolsai.jupyter-renderers`
    - `ms-toolsai.datawrangler`
    - `mhutchie.git-graph`
    - `GitHub.remotehub`
    - `GitHub.copilot`
    - `GitHub.copilot-chat`
      
Note: you will need to repeat this step once you log on to HTCF. A button will appear on these extensions giving you the option to also install on the remote machine. This will install the extension to your home folder on HTCF.

You can list all installed extensions with their versions by running ```code --list-extensions --show-versions```.

### 2. Configuring VSCode to connect to HTCF and edit files on the server directly
While still on your local machine: 
- Select open <img width="86" alt="image" src="https://github.com/dbaldridge-lab/htcf/assets/50468813/2ec5756e-5918-475e-b713-d0c0d1f41082">

- Select your home folder and press Open <img width="117" alt="image" src="https://github.com/dbaldridge-lab/htcf/assets/50468813/8409a121-5d79-406e-aa17-4098e159c7c8">

- In the left-hand pane, scroll through the files in your home folder and check if you have a config file in .ssh:

<img width="227" alt="image" src="https://github.com/dbaldridge-lab/htcf/assets/50468813/973bf943-5793-4684-bf90-1147b5054d08">

- If the ssh folder does not exists on your machine, create one by entering the following at the prompt and pressing enter:

```mkdir ~/.ssh & touch ~/.ssh/config & chmod 700 ~/.ssh & chmod 600 ~/.ssh/config```

- Create an SSH config entry for the cluster in ~/.ssh/config. You can double click on that file to open it. Enter the following in ~/.ssh/config, substituting your username and save.
```
Host htcf
Hostname login.htcf.wustl.edu
User yourusername
ControlMaster auto
ControlPath ~/.ssh/control:%h:%p:%r
```
- Test that the above entry works by opening a terminal <img width="26" alt="image" src="https://github.com/dbaldridge-lab/htcf/assets/50468813/4fcc5b5a-3373-424b-8552-a917632a7dbe">
and running `ssh htcf`. If you are prompted for a password and are able to log on, proceed.
- An additional way to login is to launch the command palette (`Cmd+Shift+P` or `F1`) and enter "remote-ssh" to show available options. Selecting "Connect to Host" should now show you a list of entries available in ~/.ssh/config. 
- You should see an htcf entry

<img width="613" alt="image" src="https://github.com/dbaldridge-lab/htcf/assets/50468813/a9e712ca-c8f5-4bee-974f-7fdb30e7cbd6">

- Upon first connection, it will install a small vscode server into your home directory. If you do no have enough space the installation will fail at which point you'll need to clean up additional space in your home directory.

---
