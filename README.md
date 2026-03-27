## UHAS Bacterial Genomics (Dry Lab Workflow)

This repository documents the dry lab component of the Bacterial Genomics training at the University of Health and Allied Sciences (UHAS). The work focuses on whole-genome read alignment and processing of bacterial sequencing data using standard bioinformatics tools in a Linux environment.

## Overview

The workflow uses a single *Escherichia coli* sample (SRR36879872) to demonstrate a complete alignment pipeline, from raw data retrieval to generation of analysis-ready files. The final outputs are sorted and indexed BAM files suitable for visualization in IGV and for downstream analyses.

## Workflow Summary

The pipeline follows these steps:

1. **Data Retrieval**
   - Download raw sequencing data from the Sequence Read Archive (SRA) using `prefetch`.

2. **FASTQ Conversion**
   - Convert `.sra` files to paired-end FASTQ format using `fasterq-dump`.

3. **Quality Control**
   - Assess read quality using `FastQC`.

4. **Reference Genome Preparation**
   - Download *E. coli* reference genomes.
   - Decompress and index the reference using `bwa index`.

5. **Read Alignment**
   - Align paired-end reads to the reference genome using `bwa mem`.

6. **File Conversion and Processing**
   - Convert SAM to BAM (`samtools view`)
   - Sort BAM files (`samtools sort`)
   - Index BAM files (`samtools index`)

7. **Alignment Evaluation**
   - Generate summary statistics using `samtools flagstat`.

## Tools and Dependencies

The following tools are required:

- NCBI Entrez Direct
- SRA Toolkit
- FastQC
- BWA
- SAMtools

Install on Ubuntu using:

```bash
sudo apt update
sudo apt install -y ncbi-entrez-direct sra-toolkit fastqc bwa samtools
