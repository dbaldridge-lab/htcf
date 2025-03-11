## Installing new software
Start an interactive session prior to beginning installation. 
If the install is expected to take a significant amount of time, consider submitting a bash script using sbatch. 

First, confirm that the software has not already been installed:
1. Check the lab software folder
   ```
   cd /ref/dblab/software
   ```
3. Check the spack lab instance:
   ```
   spack find -x
   ```

Next, consult the software's documentation. 
1. Ensure dependancies are met.
2. Look for suggested installation steps.

Not all software can be installed using spack. To see if the software exists as a spack package:
```
spack list yourKeyword
```
Available packages are also searchable [here.](https://packages.spack.io/)

Install the package to the lab spack instance:
```
spack install yourSpackPackage
```

The package can now be added to a spack environment.

## Adding spack packages to an existing environment
Display all spack environments that exist in the lab spack instance:
```
spack env list
```
Activate one of the pre-existing environments:
```
spack env activate -p yourEnvironment
```
View the spack packages that are already in the environment. 
The x flag is used to omit dependancies.
```
spack find -x
```
Add spack packages, seperating each with a space. 
Use @ to denote version:
```
spack add samtools python@3.10.4  # add spack packages
```
Exit the environment:
```
spack env deactivate
```
Reactivate the environment:
```
spack env activate -p yourEnvironment
```
Finalize the new updates:
```
spack concretize
```

## Adding modules to python in a spack environment
Activate one of the pre-existing environments:
```
spack env activate -p yourEnvironment
```
Check if pip is installed.
```
python3 -m pip --version
```
If pip is not working, try to install it. 
``` 
python3 -m ensurepip
```
If that doesn't work, upgrade pip to the latest version.
```
python -m pip install --upgrade pip
```
Load new python modules using the pip installer:
```
python3 -m pip install yourModule yourModule2
```
To confirm that a module was loaded:
1. Invoke the python interpreter
   ```
   python3
   ```
2. Run a test command
   ```
   yourModule
   ```
3. Exit python interactive mode
   ```
   exit
   ```

Adding spack packages to an environment will wipe out existing python modules.
Prior to adding new spack packages, back up your pip environment:
```
python3 -m pip freeze > my-reqs.txt
```
Reinstall after concretization:
```
python3 -m pip install -r my-reqs.txt
```

## Creating a new environment

Create a new environment if there is a specific set of software and dependancies that you want to isolate and be able to reload in future sessions.
```
spack env create newEnvName
```
Activate the new environment:
```
spack env activate -p newEnvName
```
Add spack packages, seperating each with a space. Use @ to denote version of a spack spec:
```
spack add samtools python@3.10.4  # add spack packages
```




