# Pynnotator

New release 0.4!

This is a Python Framework developed to annotate VCF files (Exomes or Genomes) from Humans.

This tools is built on state-of-the-art tools and databases for annotating VCFs.

Currently, it can only annotate VCFs generated from build GRCh37.


Tools
=====

- htslib (1.4)
- vcftools (0.1.14)
- snpeff (SnpEff 4.3k)
- vep (version 88)

Databases
=========

- 1000Genomes (Phase 3) - ALL.wgs.phase3_shapeit2_mvncall_integrated_v5b.20130502.sites.vcf 
- dbSNP (including clinvar) - (human_9606_b150_GRCh37p13)
- Exome Sequencing Project - ESP6500SI-V2-SSA137.GRCh38-liftover
- dbNFSP 3.2a (including dbscSNV 1.1)
- Ensembl 88 (phenotype and clinically associated variants)

Features
========

- Multithread Efficient!
- Annotate a VCF file using multiple VCFs as a reference
- Combine the best tools available for annotation

Files
=====

::
    .
    ├── 1000genomes
    │   ├── ALL.wgs.phase3_shapeit2_mvncall_integrated_v5b.20130502.sites.vcf.gz
    │   └── ALL.wgs.phase3_shapeit2_mvncall_integrated_v5b.20130502.sites.vcf.gz.tbi
    ├── dbnsfp
    │   ├── dbNSFP3.4a.txt.gz
    │   ├── dbNSFP3.4a.txt.gz.tbi
    │   ├── dbscSNV1.1.txt.gz
    │   └── dbscSNV1.1.txt.gz.tbi
    ├── dbsnp
    │   ├── All_20170403.vcf.gz
    │   ├── All_20170403.vcf.gz.tbi
    │   ├── clinvar.vcf.gz
    │   └── clinvar.vcf.gz.tbi
    ├── decipher
    │   ├── DDG2P.csv.gz
    │   ├── HI_Predictions_Version3.bed.gz
    │   ├── HI_Predictions_Version3.bed.gz.tbi
    │   └── population_cnv.txt.gz
    ├── ensembl
    │   ├── Homo_sapiens_clinically_associated.vcf.gz
    │   ├── Homo_sapiens_clinically_associated.vcf.gz.tbi
    │   ├── Homo_sapiens_phenotype_associated.vcf.gz
    │   └── Homo_sapiens_phenotype_associated.vcf.gz.tbi
    ├── esp6500
    │   ├── esp6500si.vcf.gz
    │   └── esp6500si.vcf.gz.tbi
    ├── snpeff_data
    │   └── GRCh37.75
    └── vep_cache
        └── homo_sapiens
            └── 88_GRCh37

705 directories, 11839 files

Requirements
============

- Ubuntu 16.04 LTS
- Python 3
- At least 40GB

Installation and Running
========================

1º Method::

    docker-compose run pynnotator -i sample.vcf

2º Method::

    sudo apt-get install gcc git python3-dev zlib1g-dev virtualenvwrapper make zip
    source /etc/bash_completion.d/virtualenvwrapper
    mkvirtualenv -p /usr/bin/python3 mendelmd
    pip install cython
    pip install pynnotator
    pynnotator install



Options
=======

You can change settings of memory usage and number of cores in settings.py

Test
====
::
    pynnotator test

How to run it?
==============
::
    pynnotator -i sample.vcf
    # this will annotate using all tools and databases available

Others
======

::

    pynnotator install
    #this will install all libraries and download a compressed file with all the annotation needed
    pynnotator build
    #this will rebuild the whole dataset required from scratch (takes a few hours and requires memory)

Development
===========

::

     git clone https://github.com/raonyguimaraes/pynnotator
     python setup.py develop