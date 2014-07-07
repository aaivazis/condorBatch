
#Condor Batch Submissions



This project loops over a dirctory and submits a condor job that creates a baby out of each root file. 

# Running the script

To submit the jobs, run

```
./submit.sh
```

Which which will package all of the project files, go over every .root file in the directory designated by `submit.sh` and package it with a job that runs the designated executable.  

### The Condor Executable

After setting a few environment variables, the executable unarchives the included files and runs a root script that creates babies out of the packaged .root file. 

Once it's done, the executable copies the file from the condor temporary directory to more permanent storage.


# Customizing

Submitting a job using Condor requires building a configuration file that describes its paramters. The job descriptions are generated by `submit.sh` - enclosed by the `EOF`. The possible values for the paramters can be found <a href="http://research.cs.wisc.edu/htcondor/manual/v8.2/2_5Submitting_Job.html">here</a>. 

To change the script run by the job, change line 34 in the designated executable.

The project files for the executable are found in `include/`. Any files that your executable depend on should be placed in this directory if you want them to be packaged with the job. These files are packages by the submit script and eventually moved to the Condor temporary directory where they are unarchived by `launch.sh`. 


# Further Reading

<a href="http://research.cs.wisc.edu/htcondor/manual/v8.2/index.html">HTCondor Manual</a>

For information on using HTCondor to submit jobs to the lcg-farm: <a href="http://www.uscms.org/uscms_at_work/software_computing/batch_systems.shtml">here</a> 

For frequently asked questions concerning HTCondor: <a href="http://www.iac.es/sieinvens/siepedia/pmwiki.php?n=HOWTOs.CondorFAQs#no_output">here</a>
