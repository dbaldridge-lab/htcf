# Setting up VSCode to run Jupyter Notebooks on HTCF
[Skip to normal setup process](https://github.com/dbaldridge-lab/htcf/blob/main/jupyter_vscode.md#normal-process)

## Prerequisites
- [Visual Studio Code](https://code.visualstudio.com/) is installed on your local machine
- WUSTL microsoft account login information
- Updated ~/.bashrc file on HTCF to include "code" alias. [See instructions here.](https://github.com/dbaldridge-lab/htcf/blob/main/bashrc-howto.md)

## Do this once
### 1. Setup code command
TODO - code command setup on HTCF

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
    - `ms-vscode.remote-server`
    - `ms-python.python`
    - `ms-toolsai.jupyter`
      
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

## Normal Process

### 1. Connect to HTCF
- Click on <img width="30" alt="image" src="https://github.com/dbaldridge-lab/htcf/assets/50468813/0c830769-0088-42b5-9a32-17689f942d5e"> in the bottom left-hand corner or
Open Command Palette (Shortcut: `Cmd+Shift+P`) and type `Remote-SSH: Connect to Host...` and select it.
- Choose your configured SSH host (will be htcf if you followed the instructions above) or Add New SSH Host and type the following in the prompt: `ssh login.htcf.wustl.edu`
- Enter your password and press enter

### 2. Open Jupyter Notebook on HTCF
This process is adapted from this page:
https://kb.uconn.edu/space/SH/26626326576/Visual+Studio+Code+(VSCode)+Guide#:~:text=A%20common%20method%20of%20using,standard%20SLURM%20job%20scheduling%20process.

TODO: How to ensure VSCode Server isn't running on login node. Maybe check in terminal(outside of VSCode) using the following:

```
ps aux | grep "vscode-server"
```

To start an interactive session (assuming you have configured your ~/.bashrc):
```
sml
```

TODO - make alias for code

Start the tunnel:
```
/ref/dblab/software/vscode/code tunnel
```

You should see the following prompt:

![image](https://github.com/dbaldridge-lab/htcf/assets/50468813/030b9235-2420-4d48-ad5f-2ce31d95c252)

 Use the arrow keys to make a selection and press ENTER.
 A link and code will appear:

 ![image](https://github.com/dbaldridge-lab/htcf/assets/50468813/169cc694-46b8-480b-9788-86fdfbd6e4b9)

 Copy the code. 
 
 Press CMD and click on the link to open the page in a browser. 

 Paste the code in the page that pops up and click next. Enter your wustl key username and password.

 ![image](https://github.com/dbaldridge-lab/htcf/assets/50468813/85ca0ab3-72c7-45db-aa22-f1e5ca4678ff)

The node your tunnel was created on will be listed. 

![image](https://github.com/dbaldridge-lab/htcf/assets/50468813/c316ddb8-56fb-466f-a112-74ebbad6c647)

At this point you have the options to:
- work with VSCode in the browser OR
- continue with the instructions below if you'd prefer to use the desktop application

TODO: Confirm whether you need to leave the current window open.

Open a new VSCode window. The shortcut is Shift + cmd + N.

Click the icon for the Remote Explorer:
![image](https://github.com/dbaldridge-lab/htcf/assets/50468813/02779d19-a100-43ad-8e23-26f15c17463a)

You should see the tunnel to the node you just created.

![image](https://github.com/dbaldridge-lab/htcf/assets/50468813/295da8d0-444b-4a12-8cfa-f5a0a784e3bb)

Click on the arrow to open the tunnel in the current window.

<img width="830" alt="image" src="https://github.com/dbaldridge-lab/htcf/assets/50468813/35b5527f-93ba-4359-98ff-be02d37100e2">

TODO - troubleshoot why I am not seeing the node I created a tunnel to on the squeue list but still seeing it as a remote and saying it is connected in bottom left hand corner:

![image](https://github.com/dbaldridge-lab/htcf/assets/50468813/e047f45d-c9de-4a7d-97ba-9d985c5913ad)

![image](https://github.com/dbaldridge-lab/htcf/assets/50468813/28c0885d-bc3b-4429-bf46-ee3e69a69020)

Confirm if the VSCode server is running on the current node listed in your prompt:

![image](https://github.com/dbaldridge-lab/htcf/assets/50468813/e5a52d4f-edf9-4f6b-83cb-e86303e835e0)

You should see something like the first three lines shown above. The fourth line is the grep command itself.

https://code.visualstudio.com/docs/remote/tunnels#_using-the-vs-code-ui

Per copilot:
"you do not need to keep the terminal window open where you started the Visual Studio Code server. Once the server is started, it runs in the background on the remote machine. You can close the terminal window or even disconnect from the SSH session, and the server will continue to run.

However, if you close the Visual Studio Code window that is connected to the remote server, the server will shut down after a period of inactivity (by default, 3 hours). This is to prevent the server from consuming resources on the remote machine when it's not being used."

"
GitHub Copilot
I see, you want to ensure that the Visual Studio Code server is running on the correct node in your HPC environment.

When you establish an SSH tunnel, Visual Studio Code runs the server on the machine you're connected to via SSH. If you're connected to a node named n013, the VS Code server should be running on n013, not on a different node.

To confirm this, you can check the process list on the remote machine. After connecting to the remote machine, open the integrated terminal in VS Code (View -> Terminal or `Ctrl+``) and run the following command:

server
This command will list all processes related to vscode-server. You should see a process for the VS Code server running on the current machine. If the VS Code server was running on a different machine, it wouldn't show up in this list.

Remember, each SSH tunnel is independent and tied to the machine you're connected to. If you connect to n013 and start an SSH tunnel, VS Code will run the server on n013. If you then connect to n002 and start another SSH tunnel, VS Code will run another server on n002. The two servers are separate and don't interfere with each other.

catchambers
So why is it called n002 even though I am on n013

GitHub Copilot
The naming of the SSH tunnel in Visual Studio Code (like n002) is an internal identifier used by VS Code for managing multiple SSH connections. It doesn't necessarily reflect the hostname of the remote machine you're connected to.

The naming scheme used by VS Code for SSH tunnels is not publicly documented and doesn't seem to be customizable. It's likely based on the order in which the connections were established or some other internal logic.

Unfortunately, this means that the name of the SSH tunnel in VS Code might not match the actual hostname of the remote machine (n013 in your case). This can be confusing, but it doesn't affect the functionality of the SSH tunnel or the VS Code server running on the remote machine.

If you need to know the actual hostname of the remote machine, you can use the hostname command in the terminal, as I mentioned in a previous message. This will tell you the hostname of the machine you're currently connected to, regardless of the name of the SSH tunnel in VS Code."



