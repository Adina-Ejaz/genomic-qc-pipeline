# Project Log

## Day 1 — Project Setup

**Date:** 21 September 2026

### Project objective

The aim of this project is to develop an automated genomic sequencing quality-control pipeline. The system will analyse sequencing data, assess selected quality metrics, identify potential quality issues, and generate an interpretable QC report.

### Today's goals

* Understand the basic purpose and structure of FASTQ files.
* Obtain a small public FASTQ dataset.
* Install FastQC.
* Run FastQC on the dataset.
* Examine the generated quality-control report.
* Set up the GitHub repository and project structure.


### Work completed

- Created the GitHub repository and initial project structure.
- Obtained a publicly available sequencing dataset from the NCBI Sequence Read Archive (SRA).
- Downloaded the sequencing data in FASTQ format.
- Installed and ran FastQC on the FASTQ dataset.
- Generated and examined the FastQC quality-control report.
- Reviewed the main quality-control categories provided by FastQC.

### What I learned

- FASTQ is a common format for storing sequencing reads together with their per-base quality information.
- Sequencing quality should be assessed before downstream genomic analysis.
- FastQC can automatically examine several characteristics of sequencing data and produce a quality-control report.
- Quality-control metrics can help identify potential issues in sequencing data.
- The FastQC report provides both individual quality checks and an overall summary using pass, warning and fail indicators.
### Practical work completed

- Downloaded the SRR1091086 sequencing dataset in FASTQ format.
- Ran FastQC on the downloaded FASTQ file.
- Examined the resulting FastQC report and its quality-control categories.
### Problems / questions encountered

- Need to understand the interpretation of individual FastQC metrics in more detail.
- Need to determine which quality metrics will be relevant for the automated QC pipeline.

### Next steps

- Learn the meaning of the main FastQC quality metrics.
- Understand how quality thresholds can be used to identify potential sequencing problems.
- Begin planning how FastQC results could be extracted and processed automatically using Python.
