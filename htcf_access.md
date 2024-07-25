## Connect to the network
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

You are now in a HTCF login shell. **Do NOT execute any heavy computation in the login shell.** Instead, there are two ways to execute your computation jobs listed below.

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

Use one of these two methods for executing computation:

1. **Interactive session**: Interactive sessions are useful for quick tasks, troubleshooting, or developing code.
To start an interactive job on a single node for a job requiring 8G of memory, use the following command. You may change the memory quota for heavy computation. 
```
srun --mem=8G --cpus-per-task=1 -J interactive -p interactive --pty /bin/bash -l
```

2. **SBATCH job**: Submit a SBATCH job to the SLURM scheduler. Once your job exits the queue it will run in the background.  This is useful when your task needs many resources (e.g. multiple threads, time). More information is provided in the [documentation](https://slurm.schedmd.com/documentation.html).


To submit an SBATCH job requiring a single node and 8G of memory that will take less than 6 hours, you must first create a script following this template:
```
#!/bin/bash

#SBATCH --job-name=my_job ## name job to make identification in the queue easier
#SBATCH --nodes=1 ## the number of nodes needed to run the job
#SBATCH --mem=8gb ## the total memory required to complete the job. suffixes specify units (e.g., G = gigabyte). if memory exceeds this the job will be cancelled.
#SBATCH --time=06:00:00 ## the max amount of time your job will run for. if it exceeds this time it will be cancelled.
#SBATCH --output=my_job.out ## name of file containing standard output streams
#SBATCH --error=my_job.err ## name of file containing standard error streams

date ## this will print the time the job started in my_job.out
hostname ## this will print the nodes the job is running on 

[insert your code]

date ## this will print the time the job finished 
```

If the script created above is called "my_script.sbatch", then submit your job script as follows:
```
sbatch my_script.sbatch
```
After submission, check your the job progress.
```
squeue -u <your_account_ID>
```
For more sophisticated parallelization, check out the [instructions on how to run a job array](https://htcf.wustl.edu/docs/runningjobs/).


(Adapted from HTCF documentation by Emma Johnson and Yiming Kang)


