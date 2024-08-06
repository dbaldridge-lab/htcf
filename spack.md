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

spack list -x # show spack specs that were explicitly installed (not including dependancies)
If you want to add more spack packages you can do spack add <package>then spack concretize.(After you reactivate the spack environment)
However this might wipe out your python environment packages so you should be sure to back up your pip environment with
python3 -m pip freeze > my-reqs.txt
and then reinstall after concretization with
python3 -m pip install my-reqs.txt


PYTHONPATH=/ref/dblab/software/spack-0.21.0/var/spack/environments/jupyter/.spack-env/view/lib/python3.10/site-packages:.
