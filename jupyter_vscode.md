# Setting up VSCode to run Jupyter Notebooks on HTCF

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

### 2. Connecting to Login/Interactive nodes to edit files directly in VSCode. 
VS code excludes certain hidden files from the file explorer by default. To show hidden files, go to settings and type exclude to adjust the patterns shown in the explorer. The shortcut `Cmd+,` can be used to open the settings menu.

Create an SSH config entry for the cluster in ~/.ssh/config . If the ssh folder does not exists on your machine create one by entering the following at the prompt and pressing enter:

```mkdir ~/.ssh & touch ~/.ssh/config & chmod 700 ~/.ssh & chmod 600 ~/.ssh/config```

If you open your home folder in VSCode, refresh and you should see something like this:

<img width="227" alt="image" src="https://github.com/dbaldridge-lab/htcf/assets/50468813/973bf943-5793-4684-bf90-1147b5054d08">

Enter the following in your ~/.ssh/config, substituting your username and save. (The control path entry allows VSCode to reuse the existing SSH connection to the cluster).
```
Host htcf
Hostname login.htcf.wustl.edu
User yourusername
ControlMaster auto
ControlPath ~/.ssh/control:%h:%p:%r
```

With the home folder open, you can double click on that file you can open it and edit it.
<img width="412" alt="image" src="https://github.com/dbaldridge-lab/htcf/assets/50468813/71b35525-cece-466f-b5f4-8bfd7a587f87">

- Test that the above entry works by opening a terminal and running 'ssh htcf'. If things look OK proceed. 
- Launch the command palette (`Cmd+Shift+P` or `F1`) and enter "remote-ssh" to show available options. Selecting "Connect to Host" should now show you a list of entries available in ~/.ssh/config. 
- Select the "htcf" entry, it should now prompt for a password. 
- Upon first connection, it will install a small vscode server into your home directory. If you do no have enough space the installation will fail at which point you'll need to clean up additional space in your home directory.
  
### 2. Configure SSH for Remote Connection
- Open Command Palette (Shortcut: `Cmd+Shift+P`)
- Type `Remote-SSH: Open SSH Configuration File` and select it
- Add your SSH configuration details

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
