# Running Jupyter Notebooks on HTCF

### 1. Connect to HTCF
- Click on <img width="30" alt="image" src="https://github.com/dbaldridge-lab/htcf/assets/50468813/0c830769-0088-42b5-9a32-17689f942d5e"> in the bottom left-hand corner or
Open Command Palette (Shortcut: `Cmd+Shift+P`) and type `Remote-SSH: Connect to Host...` and select it.
- Choose your configured SSH host (will be htcf if you followed the instructions above) or Add New SSH Host and type the following in the prompt: `ssh login.htcf.wustl.edu`
- Enter your password and press enter

### 2. Tunnel to VSCode
NOTE: if `code` command setup has not been setup but you would like to proceed, use `/ref/dblab/software/vscode/code` in place of `code`

This process is adapted from this page:
https://kb.uconn.edu/space/SH/26626326576/Visual+Studio+Code+(VSCode)+Guide#:~:text=A%20common%20method%20of%20using,standard%20SLURM%20job%20scheduling%20process.

Start an interactive session (assuming you have configured your ~/.bashrc):
```
sml
```

Start a tunnel:
```
code tunnel
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

Leave the current window open. 
Open a new VSCode window. The shortcut is `Shift + CMD + n`.

Click the icon for the Remote Explorer:
![image](https://github.com/dbaldridge-lab/htcf/assets/50468813/02779d19-a100-43ad-8e23-26f15c17463a)

You should see the tunnel to the node you just created.

![image](https://github.com/dbaldridge-lab/htcf/assets/50468813/295da8d0-444b-4a12-8cfa-f5a0a784e3bb)

Click on the arrow to open the tunnel in the current window.

<img width="830" alt="image" src="https://github.com/dbaldridge-lab/htcf/assets/50468813/35b5527f-93ba-4359-98ff-be02d37100e2">.



### 3. Jupyter Notebook setup

Enter the following command in the terminal of the new window you opened previously. This activates a spack environment that has been setup with the software and python packages needed to run the lab's Jupyter notebooks.
```
spack env activate -p jupyter
```

Open a pre-existing Jupyter notebook file.

Click the kernel selector icon:
![image](https://github.com/dbaldridge-lab/htcf/assets/50468813/bf38db53-b56f-4107-907e-65aa8b159be4)

Select the kernel you created.


#### Troubleshooting
**VSCode can't find the kernel in a spack environment**
Navigate to where the kernel spec was installed, which is typically in a folder in the following location:
```
cd $HOME/.local/share/jupyter/kernels
```

Enter the directory with the name matching the kernel that was installed. You should see a file, `kernel.json`. Print this file to the terminal:
```
cat kernel.json
```

Copy the path to the spack environment's python interpreter.
![image](https://github.com/user-attachments/assets/978a628d-a739-43aa-946c-fc383c09b6d8)

Open settings from the menu in the upper right hand corner. 

![image](https://github.com/user-attachments/assets/b2326da5-eb31-4c58-bed1-bc2fa39a28ce)
![image](https://github.com/user-attachments/assets/a580f78b-43b8-4d46-8f08-cb23aa93e38f)

**Creating a kernel for a new environments**

```
Occassionally, you may need to set up a python kernel spec for a new environment. After activating your new environment and installing all required software, enter the commands below: 
```
python3 -m ensurepip
python3 -m pip install ipykernel
python3 -m ipykernel install --user --name=your_env_name --display-name your_env_display_name
```

Unfortunatley, VSCode can't easily locate the interpreter in spack environments. For this reason, you may run in to fewer issues using conda or a python virtual environments when working Jupyter notebooks.






