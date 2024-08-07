# Spack Environments


## Adding spack packages to existing environments
The following command will display all spack environments that exist in the lab spack instance.
```
spack env list
```

Activate an environment:
```
spack env activate -p yourEnvironment
```
spack add <package>
despacktivate
spack concretize.(After you reactivate the spack environment)
However this might wipe out your python environment packages so you should be sure to back up your pip environment with
python3 -m pip freeze > my-reqs.txt
and then reinstall after concretization with
python3 -m pip install my-reqs.txt

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
spack install
python3 -m ensurepip
python3 -m pip install pysam # (can add multiple packages at once, seperate with space)
exit
```



