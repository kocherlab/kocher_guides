##########################
RNA-seq Tools and Analyses
##########################

********************
Quality Control (QC)
********************
“Garbage in, garbage out” is a concept popular among bioinformaticians to highlight an immutable truth; the quality of an analysis (i.e. the output) is dependent on the quality of the input. Therefore, most bioinformatic pipelines begin with QC steps to identify and remove data that may be detrimental to an analysis. 

All QC programs may imported using:

.. code-block:: bash
   :name: kocher_QC

   conda activate kocher_QC

FastQC
======
A straightforward method to identify quality concerns within BAM, SAM or fastq files. “FastQC aims to provide a simple way to do some quality control checks on raw sequence data coming from high throughput sequencing pipelines. It provides a modular set of analyses which you can use to give a quick impression of whether your data has any problems of which you should be aware before doing any further analysis.” The output from FastQC is an HTML file that may be viewed in any browser (e.g. chrome) :numref:`(Fig. %s) <fastQC_fig>`. The output contains eleven sections flagged as either *Pass* (green check mark), *Warn* (yellow exclamation mark), or *Fail* (red X). It should be noted that all sections of the output should be examined, rather than just sections marked as *Warn* and *Fail*, to determine the best selection of  filters to apply.

.. figure:: RNA_seq/fastQC.jpg
    :width: 100%
    :align: center
    :figclass: align-center
    :name: fastQC_fig
     
    FastQC Output

Usage
-----
.. code-block:: bash
   :name: FastQC

   # Running FastQC on a single file
   fastqc KMT5L_D05.fq.gz

   # Running FastQC on multiple files
   fastqc KMT5L_D05.fq.gz KMT6L_A04.fq.gz KMT6L_A12.fq.gz

Useful Links
------------
* `Documentation <https://www.bioinformatics.babraham.ac.uk/projects/fastqc/Help/>`_
* `Reference \(website\) <http://www.bioinformatics.babraham.ac.uk/projects/fastqc/>`_
* `Github <https://github.com/s-andrews/FastQC>`_

fastp
=====
A comprehensive and rapid filtering method for fastq files. “[fastp] can perform quality control, adapter trimming, quality filtering, per-read quality pruning and many other operations with a single scan of the fastq data”. Most analyses will require at least two operations from fastp: 1) adapter trimming and 2) per read trimming by quality score. 

Adapter trimming includes various options from defining adapter sequences on the command-line to adapter auto-detection; adapter trimming may also be disabled, if desired. 

Trimming by quality score includes three methods:
* **cut_front**:  move a sliding window 5' to 3’, drop the bases in the window if its mean quality is below a specified threshold.
* **cut_tail**:  move a sliding window 3' to 5’, drop the bases in the window if its mean quality is below a specified threshold. 
* **cut_right**:  move a sliding window 5' to 3’, if the mean quality of a window is below a specified threshold, drop the window and the sequence to the right (i.e. 3’).
Many of these methods may be altered to be similar to functions within the `Trimmomatic package <http://www.usadellab.org/cms/?page=trimmomatic>`_, if desired.

The output from fastp is an HTML file that may be viewed in any browser (e.g. chrome) :numref:`(Fig. %s) <fastp_fig>` and a JSON file that may be used for further interpreting. The HTML contains details on the input before and after the filtering process.


.. figure:: RNA_seq/fastp.jpg
    :width: 100%
    :align: center
    :figclass: align-center
    :name: fastp_fig
     
    fastp Output


Usage
-----
.. code-block:: bash
   :name: fastp

   # Single end data
   fastp -i KMT5L_D05.fq.gz -o KMT5L_D05.filtered.fq.gz

   # Paired end data
   fastp -i KMT5L_D05.R1.fq.gz -I KMT5L_D05.R2.fq.gz -o KMT5L_D05.filtered.R1.fq.gz -O KMT5L_D05.filtered.R2.fq.gz

   # Paired end data with paired end adapter auto-detection
   fastp -i KMT5L_D05.R1.fq.gz -I KMT5L_D05.R2.fq.gz -o KMT5L_D05.filtered.R1.fq.gz -O KMT5L_D05.filtered.R2.fq.gz --detect_adapter_for_pe

   # Paired end data using the the cut_right method with a
   # window size of 3 and a mean Phred quality of 20
   fastp -i KMT5L_D05.R1.fq.gz -I KMT5L_D05.R2.fq.gz -o KMT5L_D05.filtered.R1.fq.gz -O KMT5L_D05.filtered.R2.fq.gz --cut_right --cut_right_window_size 3 --cut_right_mean_quality 20

Useful Links
------------
* `Documentation <https://github.com/OpenGene/fastp/blob/master/README.md>`_
* `Reference \(Chen et al\.\, 2018\) <https://academic.oup.com/bioinformatics/article/34/17/i884/5093234>`_
* `Github <https://github.com/OpenGene/fastp>`_
* `Phred scores <https://en.wikipedia.org/wiki/Phred_quality_score>`_

**************
Read Alignment
**************
