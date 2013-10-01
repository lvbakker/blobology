For: github.com/blaxterlab/blobology/blob/master/README.md

Blobology
=========

Blaxter Lab, Institute of Evolutionary Biology, University of Edinburgh

**Goal**: To create blobplots or Taxon-Annotated-GC-Coverage plots (TAGC plots) to visualise the contents of genome assembly data sets as a QC step.

This repository accompanies the paper:  
**Blobology: exploring raw genome data for contaminants, symbionts and parasites using taxon-annotated GC-coverage plots.**
*Sujai Kumar, Martin Jones, Georgios Koutsovoulos, Michael Clarke, Mark Blaxter*  
(submitted 2013-10-01 to *Frontiers in Bioinformatics and Computational Biology special issue : Quality assessment and control of high-throughput sequencing data*).

It contains bash/perl/R scripts for running the analysis presented in the paper to create a preliminary assembly, and to create and collate GC content, read coverage and taxon annotation for the preliminary assembly, which can be visualised, such as Figure 2a from the paper showing TAGC plots/blobplots for *Caenorhabditis* sp. 5:
![Figure 2a. Caenorhabditis sp. 5 prelim assembly blobplot](https://raw.github.com/blaxterlab/blobology/master/pa61-scaffolds.fa.bowtie2.txt.taxlevel_order.01.png)

**Note**: This is an update to the code at github.com/sujaikumar/assemblage which was used in my thesis. I could have updated the code in that repository, but enough things have changed (the basic file formats as well) that I thought it made sense to create a new repo. Please use this version from now on.

Installation
------------

    git clone git://github.com/blaxterlab/blobology.git

You also need the following software:

1.  samtools (tested with version 0.1.19) http://sourceforge.net/projects/samtools/files/samtools/0.1.19/
2.  R (tested with version 2.15.2)
3.  ggplot2, an R graphics package (tested with ggplot2_0.9.3.1)
4.  ABySS - optional if you already have a preliminary assembly from another assembler (tested with version 1.3.6, compiled with mpi) - http://www.bcgsc.ca/platform/bioinfo/software/abyss/releases/1.3.6
5.  fastq-mcf - not needed if you already have quality and adapter trimmed reads (from the ea-utils suite, tested with version 1.1.2-537) - https://ea-utils.googlecode.com/files/ea-utils.1.1.2-537.tar.gz  

And the following databases:

1.  NCBI nt blasted (download from ftp://ftp.ncbi.nlm.nih.gov/blast/db/ nt.??.tar.gz)

        wget "ftp://ftp.ncbi.nlm.nih.gov/blast/db/nt.??.tar.gz"
        for a in nt.*.tar.gz; do tar xzf $a; done
        # or, if you have gnu parallel installed, highly recommended:
        # parallel tar xzf ::: nt.*.tar.gz

2.  NCBI taxonomy dump (download from ftp://ftp.ncbi.nlm.nih.gov/pub/taxonomy/taxdump.tar.gz)

        wget ftp://ftp.ncbi.nlm.nih.gov/pub/taxonomy/taxdump.tar.gz
        tar xzf taxdump.tar.gz

    Only the nodes.dmp and names.dmp files are needed (nodes.dmp stores the taxon ids and their parent-child relationships, whereas names.dmp stores their common and scientific names)
    
    

Rerun example with Caenorhabditis sp. 5
-----------------------------------------

Run `rerun.bash` from the repository