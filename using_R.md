## Configuration

**YOU ONLY NEED TO DO THIS ONCE**

Edit your bash alias file to include aliases to more easily load the lab's R library and load R from spack:

```
echo "alias labr='export R_LIBS_SITE=/ref/dblab/software/r-envs/4.3.0'" >> ~/.bash_aliases
echo "alias runr='eval \`spack load --sh   r+external-lapack\`'" >> ~/.bash_aliases

```

Once you have completed the initial configuration, you're ready to start using R!

## AIM 1: Load and use R interactively
```
## log on to interactive node
srun -J interactive -p interactive --pty /bin/bash

## load R library (using alias)
labr

## load R software (using alias)
runr

## start R
R

## you can make sure it's loaded by checking the libraries using
.libPaths()
```

## AIM 2: Run an R script in a batch job
```
## load R library (using alias)
labr
## load R software (using alias)
runr

## run R script
Rscript my_script.R
```

## AIM 3: Update or install a package in the lab's library

Making any updates or installs has to be done in an interactive session (plus that makes troubleshooting easier). 

```
## log on to interactive node
srun -J interactive -p interactive --pty /bin/bash

## load R library (using alias)
labr

## load R (using alias)
runr

## start R
R

## set primary library to the lab's library (this will make sure all installs go in here)
.libPaths("/ref/dblab/software/r-envs/dblab_R/4.1.3")

## install package, e.g.:
install.packages("ggdogs")
```


## Troubleshooting Notes:

This section includes notes on any issues we have had installing packages and how they were fixed.

### Tidyverse

The error message: 

```
Error: package or namespace load failed for ‘tidyverse’ in loadNamespace(j <- i[[1L]], c(lib.loc, .libPaths()), versionCheck = vI[[j]]):
 there is no package called ‘xml2’
```

**The problem:** xml2 wasn't installed

**The solution:** install xml2
```
install.packages("xml2")
library(xml2)
```

### xml2

The error message: 

```
------------------------- ANTICONF ERROR ---------------------------
Configuration failed because libxml-2.0 was not found. Try installing:
 * deb: libxml2-dev (Debian, Ubuntu, etc)
 * rpm: libxml2-devel (Fedora, CentOS, RHEL)
 * csw: libxml2_dev (Solaris)
If libxml-2.0 is already installed, check that 'pkg-config' is in your
PATH and PKG_CONFIG_PATH contains a libxml-2.0.pc file. If pkg-config
is unavailable you can set INCLUDE_DIR and LIB_DIR manually via:
R CMD INSTALL --configure-vars='INCLUDE_DIR=... LIB_DIR=...'
--------------------------------------------------------------------
ERROR: configuration failed for package ‘xml2’
* removing ‘/ref/dblab/software/r-envs/dblab_R/4.1.3/xml2’
```

**The problem:** libxml software wasn't loaded in the environment

**The solution:** use spack to load libxml-2.0 IN THE SHELL, then can open R and install xml2 pkg
```
eval `spack load --sh   libxml2`
```

Note: Instructions shared by Emma Johnson, I haven't tested them
