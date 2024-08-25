# Setting up VSCode
[Skip to normal setup process](https://github.com/dbaldridge-lab/htcf/blob/main/jupyter_vscode.md#normal-process)

## Prerequisites
- [Visual Studio Code](https://code.visualstudio.com/) is installed on your local machine
- WUSTL microsoft account login information
- Updated ~/.bashrc file on HTCF to include "code" alias. [See instructions here.](https://github.com/dbaldridge-lab/htcf/blob/main/bashrc-howto.md)
- Basic understanding of how to navigate [VSCode GUI](https://code.visualstudio.com/docs/getstarted/userinterface#_views)
- Know how to open and execute commands in the [integrated terminal](https://code.visualstudio.com/docs/terminal/getting-started)

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

### 2. Install Extensions Locally
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

### 3. Install Extension on HTCF
A button will appear on some extensions giving you the option to also install on the remote machine. This will install the extension to your home folder on HTCF.

You can list all installed extensions with their versions by running `code --list-extensions --show-versions`.

### 4. Configuring SSH
While still on your local machine: 
- Open your home folder from within VSCode `File -> Open Folder`. Type `~` and press `ENTER`.
- Scroll through the files in your home folder and check if you have a config file in .ssh:
  
<img width="227" alt="image" src="https://github.com/dbaldridge-lab/htcf/assets/50468813/973bf943-5793-4684-bf90-1147b5054d08">

- If the ssh folder does not exist, create one. Enter the following at the terminal prompt:
```
mkdir ~/.ssh & touch ~/.ssh/config & chmod 700 ~/.ssh & chmod 600 ~/.ssh/config
```

- Open the file. Double click on the file in the explorer or enter `code ~/.ssh/config`.
- Paste the following in ~/.ssh/config, substituting your username and save. 
```
Host htcf
Hostname login.htcf.wustl.edu
User yourusername # change this
ControlMaster auto
ControlPath ~/.ssh/control:%h:%p:%r
```
- Test the configuration by entering `ssh htcf` at the terminal prompt. If you are prompted for a password and are able to log on, proceed.
- An additional way to login is to launch the command palette (`Cmd+Shift+P` or `F1`) and enter "remote-ssh" to show available options. You should see an htcf option.

<img width="613" alt="image" src="https://github.com/dbaldridge-lab/htcf/assets/50468813/a9e712ca-c8f5-4bee-974f-7fdb30e7cbd6">

---
