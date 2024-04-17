(Credit to Emma Johnson / Yiming Kang for this writeup)

## VPN
First things first is to connect to WUSM-secure wifi or ethernet.

If you want to work off campus, you need to use a VPN. Download the Cisco AnyConnect app and install. In the app, type in msvpn.wusm.wustl.edu for connecting address, and use accounts\<your_wustl_id> and <your_wustl_password> for authentication.

## Logging in to the cluster (Mac or Linux)
HTCF can be logged onto from your local computer on a mac or linux by using the pre-installed terminal application.
1. To open a terminal window. You can either search for "terminal" in the search bar or can navigate to the application by opening a finder window and then navigating to Applications > Utilities > Terminal.
2. Type the ssh command in the terminal, using your assigned username.

```
ssh <your_wustl_id>@login.htcf.wustl.edu
```

3. When prompted, enter ```<your_wustl_password>```. This will be the same password you use with your wustl key.

## "Hacking" the login process with a bash alias
Using an alias on your local computer, you can actually make the logon process quicker, by simply typing "logon" instead of having to type out the ssh command everytime you want to login.

1. Start up Terminal
2. Type cd ~/ to go to your home folder
3. edit your bash profile using:
```
vi .zshrc
```
and then add this line (once again replacing username):
```
alias logon="ssh username@login.htcf.wustl.edu"
```
4. run command to initialize (you only need to do this once):
```
source ~/.zshrc
```
5. Try it out! Open a new terminal window and run the "logon" command:
```
logon
```

## Running a job on the cluster

Heavy computation should not be performed on the login shell, but instead using one of two methods for executing computation:

1. an interactive session. Interactive sessions are useful for quick tasks, troubleshooting, or developing code. 
2. a slurm SBATCH job. This is useful when your task needs many resources (e.g. multiple threads, time). More information is provided in the [slurm documentation](https://slurm.schedmd.com/documentation.html).

To start an interactive session on a single node for a job requiring 2G of memory, you would use the code: 
```
srun --mem=2G --cpus-per-task=1 -J interactive -p interactive --pty /bin/bash -l
```

To submit an SBATCH job requiring a single node and 2G of memory that will take less than 6 hours, you must first create a script following this template:
```
#!/bin/bash

#SBATCH --job-name=my_job ## name job to make identification in the queue easier
#SBATCH --nodes=1 ## the number of nodes needed to run the job
#SBATCH --mem=2gb ## the total memory required to complete the job. suffixes specify units (e.g., G = gigabyte). if memory exceeds this the job will be cancelled.
#SBATCH --time=06:00:00 ## the max amount of time your job will run for. if it exceeds this time it will be cancelled.
#SBATCH --output=my_job.out ## name of file containing standard output streams
#SBATCH --error=my_job.err ## name of file containing standard error streams

date ## this will print the time the job started in my_job.out
hostname ## this will print the nodes the job is running on 

[insert your code]

date ## this will print the time the job finished 
```

If the script created above is called "my_script.sbatch", then you can submit it to the slurm scheduler using the code:
```
sbatch my_script.sbatch
```


