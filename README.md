
# MetaPatho 

# Introduction

MetaPatho is an easy-to-use, rapid, robust, and shotgun metagenomics-based tool for identifying human and plant bacterial pathogens in environmental and clinical metagenomes.

To ensure that pathogen identification pipeline remains accurate while being simple and user-friendly (e.g., avoiding the installation of complex dependencies), we developed a high-quality bacterial pathogen genome database and easily integrate the pathogen annotation module into routine metagenomic functional analysis workflows. 

This approach allows user to obtain pathogen distribution information simply by annotating against the pathogen database during standard metagenomic functional profiling, thus avoiding the need for new software installation and additional environment dependencies.

MetaPatho exhibits the following features and advantages: 

(1) the analysis is rapid and straightforward, allowing the pathogen annotation module to be conveniently integrated into standard metagenomic functional analysis processes; 

(2) establishment of a list and high-quality pathogenic databases for soil-inhabiting human (MetaPatho-HBPDB) and plant (MetaPatho-PBPDB) bacterial pathogens; 

(3) accuracy validation of our tool in detecting bacterial pathogens through both in-silico tests and soil spike-in experiments including pathogen DNA spike-in and cell spike-in tests.


# Installation and download database

The main advantage of MetaPatho is that it combines high accuracy with simplicity, speed, and user-friendliness. 

MetaPatho does not require the installation of complex software or environments and operates in just two steps: 


Step 1: download the bacterial pathogen genome database; 

Before running MetaPatho, users must download the database they need (i.e., MetaPatho-HBPDB or MetaPatho-PBPDB):

The human (MetaPatho-HBPDB) and plant (MetaPatho-PBPDB) bacterial pathogen databases have been deposited at the Figshare (https://figshare.com/s/753d3906f6faf1986d6a)




Step 2: install DIAMOND in the computing environment, as MetaPatho relies on DIAMOND for database alignment.

```bash
conda create -n MetaPatho
source activate MetaPatho
conda install diamond=2.1.8
```


About the DIAMOND:

DIAMOND is a  high-throughput program for aligning DNA reads or protein sequences against a protein reference database such as NR, at up to 20,000 times the speed of BLAST, with high sensitivity.

See the DIAMOND github page: https://github.com/bbuchfink/diamond

Cite the DIAMOND:

Buchfink B, Reuter K, Drost HG, "Sensitive protein alignments at tree-of-life scale using DIAMOND", Nature Methods 18, 366–368 (2021). doi:10.1038/s41592-021-01101-x


# Quick run

MetaPatho-HBPDB:

```bash
diamond blastp --db Database/MetaPatho-HBPDB.v1.0 --query ORF_protein.fa \
--outfmt 6 --threads 22 --max-target-seqs 1 --quiet -e 1e-10 --more-sensitive --block-size 10 \
--query-cover 70 --out HBPDB_Results/BHPDB_diamond.f6
```

MetaPatho-PBPDB:

```bash
diamond blastp --db Database/MetaPatho-PBPDB.v1.0 --query ORF_protein.fa \
--outfmt 6 --threads 22 --max-target-seqs 1 --quiet -e 1e-10 --more-sensitive --block-size 10 \
--query-cover 70 --out PBPDB_Results/PBPDB_diamond.f6
```
