# Setting up VSCode to run Jupyter Notebooks on HTCF
[Skip to normal setup process](https://github.com/dbaldridge-lab/htcf/blob/main/jupyter_vscode.md#normal-process)

## Prerequisites
- Visual Studio Code is installed on your local machine
- WUSTL microsoft account login information
- Updated ~/.bashrc file on HTCF to include "code" alias. [See instructions here.](https://github.com/dbaldridge-lab/htcf/blob/main/bashrc-howto.md)

## DO THIS ONCE
### 1. Install Extensions 
- Open VSCode on your local machine
- Go to Extensions <img width="33" alt="image" src="https://github.com/dbaldridge-lab/htcf/assets/50468813/7b07ab0f-e68f-4b33-954b-2ac556c2ddb9">
(Shortcut: `Cmd+Shift+X`)
- Search and install the following extensions:
    - `ms-vscode-remote.remote-ssh`
    - `ms-vscode.remote-server`
    - `ms-python.python`
    - `ms-toolsai.jupyter`
      
Note: you will need to repeat this step once you log on to HTCF. A button will appear on these extensions giving you the option to also install on the remote machine. This will install the extension to your home folder on HTCF.

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
- Test that the above entry works by opening a terminal and running 'ssh htcf'. If things look OK proceed. 
- Launch the command palette (`Cmd+Shift+P` or `F1`) and enter "remote-ssh" to show available options. Selecting "Connect to Host" should now show you a list of entries available in ~/.ssh/config. 
- Select the "htcf" entry, it should now prompt for a password. 
- Upon first connection, it will install a small vscode server into your home directory. If you do no have enough space the installation will fail at which point you'll need to clean up additional space in your home directory.

---

## Normal Process

### 3. Connect to Remote Server
- Open Command Palette (Shortcut: `Cmd+Shift+P`)
- Type `Remote-SSH: Connect to Host...` and select it
- Choose your configured SSH host or Add New SSH Host and type the following in the prompt:
```
ssh login.htcf.wustl.edu
``` 
- Enter your 

### 4. Open Jupyter Notebook on Remote Server
- Open Command Palette (Shortcut: `Cmd+Shift+P`)
- Type `Jupyter: Create New Blank Notebook` and select it
- Start coding in your Jupyter notebook
