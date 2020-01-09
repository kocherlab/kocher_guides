Serial Jobs
-----------

Most scripts - including a large number of bioinformatic analyses and pipelines - may be considered serial processes, as only a single task (i.e. single line of code, algorithm, function, analysis, etc.) is processed at a time. Submitting a serial job only requires the creation of a SLURM script.

.. code-block::bash
   \#!/bin/bash
   \#SBATCH --job-name=myserial-job  \# Name of the job
   \#SBATCH --nodes=1                \# Node count
   \#SBATCH --ntasks=1               \# Number of tasks across all nodes
   \#SBATCH --cpus-per-task=1        \# Cores per task (>1 if multi-threaded tasks)
   \#SBATCH --mem-per-cpu=4G         \# Memory per core (4G is default)
   \#SBATCH --time=00:01:00          \# Run time limit (HH:MM:SS)
   \#SBATCH --mail-type=all          \# Email on job start, end, and fault
   \#SBATCH --mail-user=<YourNetID>@princeton.edu
   
   echo 'Hello world!'
   echo 'This is my first SLURM script'
   echo 'Behold the power of HPCs'

Array Jobs
----------

Situations often arise when you want to run many almost identical jobs simultaneously, perhaps running the same program many times but changing the input data or some argument or parameter. One possible solution is to write a Python or Perl script to create all the slurm files and then write a BASH script to execute them. This is very time consuming and might end up submitting many more jobs to the queue than you actually need to. This is a typical problem suited to an array job.