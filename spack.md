# Spack Environments






## Creating a new environment
```
spack env create yourenvname
spack env activate -p <existing environment name>
spack add samtools python@3.9.7  # add spack specs
spack install
python3 -m ensurepip
python3 -m pip install pysam # (can add multiple packages at once, seperate with space)
exit
```

## Adding spack specs to an existing environment


spack list -x # show spack specs that were explicitly installed (not including dependancies)
spack add <package>
despacktivate
spack concretize.(After you reactivate the spack environment)
However this might wipe out your python environment packages so you should be sure to back up your pip environment with
python3 -m pip freeze > my-reqs.txt
and then reinstall after concretization with
python3 -m pip install my-reqs.txt

