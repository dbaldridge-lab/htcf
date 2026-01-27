# Running Jupyter Notebooks on HTCF
Adapted from [this page](https://kb.uconn.edu/space/SH/26626326576/Visual+Studio+Code+(VSCode)+Guide#:~:text=A%20common%20method%20of%20using,standard%20SLURM%20job%20scheduling%20process).

## Prerequisites
VSCode was installed and configured according to [these instructions.](https://github.com/dbaldridge-lab/htcf/blob/main/vscode.md)

Follow [these instructions](https://github.com/dbaldridge-lab/htcf/blob/main/tunneling.md)
to start a tunnel.

## 1. Connect to HTCF using SSH

## 2. Start an Interactive Session

## 3. Activate Environment with Jupyter Software

Activate a spack environment containing the software and python packages needed to run a Jupyter notebook. 

```
spack env activate -p jupyter
```

This assumes you have already setup this environment and named it `jupyter` in your spack distribution. [TODO: list spack packages to add]

It also assumes you have sourced the spack bash helper file, which can be [added to your bashrc file](https://github.com/dbaldridge-lab/htcf/blob/main/bashrc-howto.md)).


## 4. Setup Notebook to Execute Code
- Open or create a Jupyter notebook .ipynb file.
- Click the kernel selector icon:
![image](https://github.com/dbaldridge-lab/htcf/assets/50468813/bf38db53-b56f-4107-907e-65aa8b159be4)
- Paste in the path (edit as needed for your specific Spack instance and environment):
```
/ref/dblab/software/spack-0.21.0/var/spack/environments/jupyter/.spack-env/view/bin/python
```
- Refresh under `Jupyter Kernels` if needed

---
<img width="830" alt="image" src="https://github.com/dbaldridge-lab/htcf/assets/50468813/35b5527f-93ba-4359-98ff-be02d37100e2">


---
## Troubleshooting

### Kernel is crashing
- Try allocating more memory

### Can't find the kernel for the spack environment 
You may need to follow these steps when creating new spack environments.

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

Continue with the instructions in step 6 above, pasting in this path instead.









