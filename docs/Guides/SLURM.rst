#####
SLURM
#####

***********
Serial Jobs
***********

Most scripts - including a large number of bioinformatic analyses and pipelines - may be considered serial processes, as only a single task (i.e. single line of code, algorithm, function, analysis, etc.) is processed at a time. Submitting a serial job only requires the creation of a SLURM script.

.. code-block:: bash
   :linenos:
   :caption: myserial.slurm
   :name: myserial

   #!/bin/bash
   #SBATCH --job-name=myserial-job                 # Name of the job
   #SBATCH --output=myserial-job.%j.out            # Name of the output file (with jobID %j)
   #SBATCH --error=myserial-job.%j.err             # Name of the error file (with jobID %j)
   #SBATCH --nodes=1                               # Node count
   #SBATCH --ntasks=1                              # Number of tasks across all nodes
   #SBATCH --cpus-per-task=1                       # Cores per task (>1 if multi-threaded tasks)
   #SBATCH --mem-per-cpu=4G                        # Memory per core (4G is default)
   #SBATCH --time=00:01:00                         # Run time limit (HH:MM:SS)
   #SBATCH --mail-type=all                         # Email on job start, end, and fault
   #SBATCH --mail-user=<YourNetID>@princeton.edu   # Email address

   echo 'Hello world!'
   echo 'This is my first SLURM script'
   echo 'Behold the power of HPC'

*****************************
Multithreaded Jobs (i.e. MPI)
*****************************

Often a complex or large serial process (e.g. RNA-seq alignment, homology identification, etc.) may be accelerated using multithreading (i.e. simultaneous execution of multiple CPU threads/cores). This often results in higher computational resource usage but lower wall-time. 

.. code-block:: bash
   :linenos:
   :caption: mympi.slurm
   :name: myserial

   #!/bin/bash
   #SBATCH --job-name=mympi-job                    # Name of the job
   #SBATCH --output=mympi-job.%j.out               # Name of the output file (with jobID %j)
   #SBATCH --error=mympi-job.%j.err                # Name of the error file (with jobID %j)
   #SBATCH --nodes=1                               # Node count
   #SBATCH --ntasks=1                              # Number of tasks across all nodes
   #SBATCH --cpus-per-task=10                      # Cores per task (>1 if multi-threaded tasks)
   #SBATCH --mem-per-cpu=4G                        # Memory per core (4G is default)
   #SBATCH --time=00:01:00                         # Run time limit (HH:MM:SS)
   #SBATCH --mail-type=all                         # Email on job start, end, and fault
   #SBATCH --mail-user=<YourNetID>@princeton.edu   # Email address

   blastn -query query.fasta -db db.fasta -out blast.out -num_threads 10

**********
Array Jobs
**********

Situations often arise when you want to run many almost identical jobs simultaneously, perhaps running the same program many times but changing the input data or some argument or parameter. One possible solution is to write a Python or Perl script to create all the slurm files and then write a BASH script to execute them. This is very time consuming and might end up submitting many more jobs to the queue than you actually need to. This is a typical problem suited to an array job. Below is an example of a SLURM array script (See :ref:`myarray`) that submits jobs line by line from a task file (See :ref:`slurm_jobs`). Task files are an ideal solution when running jobs with random filenames - i.e. without a repeated pattern. 


.. code-block:: bash
   :linenos:
   :caption: myarray.slurm
   :name: myarray

   #!/bin/bash
   #SBATCH --job-name=myarray-job                  # Name of the job
   #SBATCH --output=myarray.%A.%a.out              # Name of the output files (with array jobID %A, and task number %a)
   #SBATCH --error=myarray.%A.%a.err               # Name of the error files (with array jobID %A, and task number %a)
   #SBATCH --nodes=1                               # Node count
   #SBATCH --ntasks=1                              # Number of tasks across all nodes
   #SBATCH --cpus-per-task=1                       # Cores per task (>1 if multi-threaded tasks)
   #SBATCH --mem-per-cpu=4G                        # Memory per core (4G is default)
   #SBATCH --time=00:01:00                         # Run time limit (HH:MM:SS)
   #SBATCH --array=1-6%3                           # Job array, limited to 3 simultaneous tasks
   #SBATCH --mail-type=all                         # Email on job start, end, and fault
   #SBATCH --mail-user=<YourNetID>@princeton.edu   # Email address
   
   sed -n -e "$SLURM_ARRAY_TASK_ID p" slurm_jobs | srun bash

Please note: In comparison to our serial SLURM script, our array script includes two additional aruments - *%j* and *$SLURM_ARRAY_TASK_ID*. *%j* is used to add the job id to our stdout/stderr output files, thus resulting in a set of stdout/stderr files for each task. *$SLURM_ARRAY_TASK_ID* is used to assign the current task ID (1, 2, 3, etc.) from *#SBATCH --array=1-6*. The IDs are then used by the *sed* command to run the relevant line number. 
   
.. code-block:: bash
   :linenos:
   :caption: slurm_jobs
   :name: slurm_jobs

   echo 'Line 1'
   echo 'Line 2'
   echo 'Line 3'
   echo 'Line 4'
   echo 'Line 5'
   echo 'Line 6'

**********************
Additional Information
**********************

More tutorials and information on SLURM may be found at the `Introducing Slurm <https://researchcomputing.princeton.edu/slurm>`_.

