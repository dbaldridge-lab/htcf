## Loading conda in a shell script (e.g. for batch jobs)
```
# Replace with the path to your conda install
source /ref/dblab/software/c.chitwood/anaconda3/bin/activate
conda init --all
```

## Install R using conda
In a bash terminal:
```
conda install -c r r-base
```
```
conda install -c r r-irkernel
```

In an R terminal:
```
install.packages('IRkernel')
```
```
IRkernel::installspec()
```


### Using R in a notebook
Add notebook cells to select kernels:
```
#!connect jupyter --kernel-name Rkernel --conda-env base --kernel-spec ir
```
