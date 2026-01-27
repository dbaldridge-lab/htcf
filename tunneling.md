## 1. Connect to HTCF using SSH
- Use the shortcut "CMD + Shift + P", then type and select "Remote-SSH: Connect to Host"
- Choose the SSH host [configured previously](https://github.com/dbaldridge-lab/htcf/blob/main/vscode.md#4-configuring-ssh) or select `Add New SSH Host` and type `ssh login.htcf.wustl.edu` at the prompt
- Enter your password and press `ENTER`

## 2. Start an Interactive Session
If your `~/.bashrc` was [configured as suggested](https://github.com/dbaldridge-lab/htcf/blob/main/bashrc-howto.md), type **one** of the following in the terminal and press `ENTER` to start an interactive session:
```
sml # 5G of memory
med # 20G of memory
lrg # 100G of memory
```

Otherwise, enter this command, adjusting the memory allocated as needed:
```
srun --mem=5G --cpus-per-task=1 -J interactive -p interactive --pty /bin/bash -l
```

When you enter this command, you will see your interactive job in the queue:
```
squeue -u $USER
```

## 3. Create VSCode Tunnel to the node

In the same window, start a tunnel by entering this command in the integrated terminal, which can be viewed using the shortcut `CMD + J`:
```
code tunnel
```

![image](https://github.com/dbaldridge-lab/htcf/assets/50468813/030b9235-2420-4d48-ad5f-2ce31d95c252)

 - Use the arrow keys to select Microsoft Account and press `ENTER`

 ![image](https://github.com/dbaldridge-lab/htcf/assets/50468813/169cc694-46b8-480b-9788-86fdfbd6e4b9)

 - Copy the code
 - Press CMD and click on the link to open the page in a browser
   
 ![image](https://github.com/dbaldridge-lab/htcf/assets/50468813/85ca0ab3-72c7-45db-aa22-f1e5ca4678ff)
- Paste the code and click next
- Enter your wustl key username and password

## 4. Connect to the tunnel
### Browser
You can open the link provided in the interactive terminal where the interactive node is running the terminal to work in the browser. Hover over the link and use `CMD + click`.

### VSCode Application
Alternatively, you can work in the VSCode desktop application. You may want to do this if you use customized settings and local extensions.
- Leaving the previous VSCode window open, open a new VSCode window using the shortcut `CMD + Shift + N`.
- Click the icon for the Remote Explorer:
![image](https://github.com/dbaldridge-lab/htcf/assets/50468813/02779d19-a100-43ad-8e23-26f15c17463a)

You should see the tunnel to the node you just created.
![image](https://github.com/dbaldridge-lab/htcf/assets/50468813/295da8d0-444b-4a12-8cfa-f5a0a784e3bb)
- Click on the arrow to open the tunnel in the current window.
