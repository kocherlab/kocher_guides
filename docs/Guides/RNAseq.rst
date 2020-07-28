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
A straightforward method to identify quality concerns within BAM, SAM or FastQ files. “FastQC aims to provide a simple way to do some quality control checks on raw sequence data coming from high throughput sequencing pipelines. It provides a modular set of analyses which you can use to give a quick impression of whether your data has any problems of which you should be aware before doing any further analysis.” The output from FastQC is an HTML file that may be viewed in any browser (e.g. chrome) :numref:`(Fig. %s) <fastQC_fig>`. The output contains eleven sections flagged as either *Pass* (green check mark), *Warn* (yellow exclamation mark), or *Fail* (red X). It should be noted that all sections of the output should be examined, rather than just sections marked as *Warn* and *Fail*, to determine the best selection of  filters to apply.

.. figure:: RNA_seq/fastQC.jpg
    :width: 100%
    :align: center
    :figclass: align-center
    :name: fastQC_fig
     
    FastQC Output Example


Usage
-----
.. code-block:: bash
   :name: FastQC

   # Test
   fastqc KMT5L_D05.fq.gz

Useful Links
------------
* `Documentation <https://www.bioinformatics.babraham.ac.uk/projects/fastqc/Help/>`_
* `Reference \(website\) <http://www.bioinformatics.babraham.ac.uk/projects/fastqc/>`_
* `Github <https://github.com/s-andrews/FastQC>`_

fastp
=====
A comprehensive and rapid filtering method for FastQ files. “[FastQ] can perform quality control, adapter trimming, quality filtering, per-read quality pruning and many other operations with a single scan of the FASTQ data.”

Usage
-----
.. code-block:: bash
   :name: fastp

   fastp -i KMT5L_D05.fq.gz -o KMT5L_D05.filtered.fq.gz

Useful Links
------------
* `Documentation <https://github.com/OpenGene/fastp/blob/master/README.md>`_
* `Reference \(Chen et al\.\, 2018\) <https://academic.oup.com/bioinformatics/article/34/17/i884/5093234>`_
* `Github <https://github.com/OpenGene/fastp>`_

**************
Read Alignment
**************
