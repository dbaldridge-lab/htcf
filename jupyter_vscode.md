# Setting up VSCode to run Jupyter Notebooks on HTCF

## Prerequisites
- Visual Studio Code is installed on your local machine
- WUSTL microsoft account login information
- Updated ~/.bashrc file on HTCF to include "code" alias. [See instructions here.](https://github.com/dbaldridge-lab/htcf/blob/main/bashrc-howto.md)

## DO THIS ONCE
### 1. Install Extensions
- Open VSCode on your local machine
- Go to Extensions (Shortcut: `Cmd+Shift+X`)
- Search and install the following extensions:
    - `ms-vscode-remote.remote-ssh`
    - `ms-vscode.remote-server`
    - `ms-python.python`
    - `ms-toolsai.jupyter`
      
Note: you will need to repeat this step once you log on to HTCF. A button will appear on these extensions giving you the option to also install on the remote machine. This will install the extension to your home folder on HTCF.

### 2. Connecting to Login/Interactive nodes to edit files directly in VSCode. 
Create an SSH config entry for the cluster in ~/.ssh/config . If the ssh folder does not exists on your machine create one by entering the following at the prompt and pressing enter:

```mkdir ~/.ssh & touch ~/.ssh/config & chmod 700 ~/.ssh & chmod 600 ~/.ssh/config```

Enter the following in your ~/.ssh/config, substituting your username and save. (The control path entry allows VSCode to reuse the existing SSH connection to the cluster).
```
Host htcf
Hostname login.htcf.wustl.edu
User yourusername
ControlMaster auto
ControlPath ~/.ssh/control:%h:%p:%r
```
First test that the above entry works by opening a terminal and running 'ssh hpc'. If things look OK proceed. 
Launch VSCode, navigate to extensions. Search for and install the "remote-ssh" extension provided by Microsoft.
Launch the command palette (Shift Command P or F1) and enter "remote-ssh" to show available options. Selecting "Connect to Host" should now show you a list of entries available in ~/.ssh/config. 
Select the "HPC" entry, it should now prompt for both the password and Duo multifactor authentication. 
Upon first connection, it will install a small vscode server into your home directory. If you do no have enough space the installation will fail at which point you'll need to clean up additional space in your cluster home dir. 
### 2. Configure SSH for Remote Connection
- Open Command Palette (Shortcut: `Cmd+Shift+P`)
- Type `Remote-SSH: Open Configuration File` and select it
- Add your SSH configuration details
![alt text](image.png)

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
