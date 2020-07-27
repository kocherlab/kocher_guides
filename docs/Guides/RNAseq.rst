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
A straightforward method to identify quality concerns within BAM, SAM or FastQ files. “FastQC aims to provide a simple way to do some quality control checks on raw sequence data coming from high throughput sequencing pipelines. It provides a modular set of analyses which you can use to give a quick impression of whether your data has any problems of which you should be aware before doing any further analysis.”

Usage
-----
.. code-block:: bash
   :name: FastQC

   fastqc KMT5L_D05.fq.gz

Reference
---------
`Software Website <http://www.bioinformatics.babraham.ac.uk/projects/fastqc/>`_.

Other Links
-----------
`Github <https://github.com/s-andrews/FastQC>`_.

fastp
=====
A comprehensive and rapid filtering method for FastQ files. “[FastQ] can perform quality control, adapter trimming, quality filtering, per-read quality pruning and many other operations with a single scan of the FASTQ data.”

Usage
-----
.. code-block:: bash
   :name: fastp

   fastp -i KMT5L_D05.fq.gz -o KMT5L_D05.filtered.fq.gz

Reference
---------
`Chen et al``.,`` 2018 <https://academic.oup.com/bioinformatics/article/34/17/i884/5093234>`_.

Other Links
-----------
`Github <https://github.com/OpenGene/fastp>`_.

**************
Read Alignment
**************