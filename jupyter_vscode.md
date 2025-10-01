# Running Jupyter Notebooks on HTCF
Adapted from [this page](https://kb.uconn.edu/space/SH/26626326576/Visual+Studio+Code+(VSCode)+Guide#:~:text=A%20common%20method%20of%20using,standard%20SLURM%20job%20scheduling%20process).

## Prerequisites
VSCode was installed and configured according to [Steps 1 and 2 in these instructions.](https://github.com/dbaldridge-lab/htcf/blob/main/vscode.md)

## 1. Connect to HTCF using SSH
- Use the shortcut "CMD + Shift + P", then type and select "Remote-SSH: Connect to Host"
- Choose the SSH host [configured previously](https://github.com/dbaldridge-lab/htcf/blob/main/vscode.md#4-configuring-ssh) or select `Add New SSH Host` and type `ssh login.htcf.wustl.edu` at the prompt
- Enter your password and press `ENTER`

## 2. Tunnel to VSCode
### (Tunneling Option 1)
Assuming your `~/.bashrc` was [configured as suggested](https://github.com/dbaldridge-lab/htcf/blob/main/bashrc-howto.md), type **one** of the following in the terminal and press `ENTER` to start an interactive session:
```
sml # 5G of memory
med # 20G of memory
lrg # 100G of memory
```

Start a tunnel:
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
- Leaving the previous VSCode window open, open a new VSCode window. The shortcut is `CMD + Shift + N`.

- Click the icon for the Remote Explorer:
![image](https://github.com/dbaldridge-lab/htcf/assets/50468813/02779d19-a100-43ad-8e23-26f15c17463a)

You should see the tunnel to the node you just created.

![image](https://github.com/dbaldridge-lab/htcf/assets/50468813/295da8d0-444b-4a12-8cfa-f5a0a784e3bb)

- Click on the arrow to open the tunnel in the current window.

## 3. Jupyter Notebook setup

Activate a spack environment containing the software and python packages needed to run a Jupyter notebook. 
```
spack env activate -p jupyter
```

- Open a pre-existing Jupyter notebook file.
- Click the kernel selector icon:
![image](https://github.com/dbaldridge-lab/htcf/assets/50468813/bf38db53-b56f-4107-907e-65aa8b159be4)
- Paste in the path (edit as needed for your specific Spack instance and environment):
```
/ref/dblab/software/spack-0.21.0/var/spack/environments/jupyter/.spack-env/view/bin/python
```
- Refresh under `Jupyter Kernels` if needed
<img width="830" alt="image" src="https://github.com/dbaldridge-lab/htcf/assets/50468813/35b5527f-93ba-4359-98ff-be02d37100e2">

---

### Creating a kernel (only required when creating new environments):

After [activating the jupyter spack environment and installing all required software](https://github.com/dbaldridge-lab/htcf/blob/main/spack.md#creating-a-new-environment), enter the commands below: 

```
python3 -m ensurepip
python3 -m pip install ipykernel
python3 -m ipykernel install --user --name=your_env_name --display-name your_env_display_name
```

Start a tunnel.

Navigate to where the kernel spec was installed, which is typically in the following location:
```
cd $HOME/.local/share/jupyter/kernels
```

Enter the directory with the name matching the kernel that was installed. Assuming you were the user that created this kernel using ipykernel, you should see a file, `kernel.json`. Print this file to the terminal:
```
cat kernel.json
```
Grab the path listed in this file.

Continue with the instructions in step 3 above, pasting in this path instead.

---
### Troubleshooting

#### Kernel is crashing
- Try allocating more memory











