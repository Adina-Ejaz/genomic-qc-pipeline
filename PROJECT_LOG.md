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

## Day 2 — Understanding QC Metrics

**Date:** 06/10/2026

### Today's goals

- Understand the main FastQC quality-control metrics.
- Identify which metrics are most relevant to the automated pipeline.
- Begin considering how QC thresholds can be applied programmatically.

### Work completed

- Reviewed the FastQC report generated from the SRR1091086 dataset.
- Examined per-base sequence quality.
- Examined per-sequence quality scores.
- Examined per-sequence GC content.
- Examined sequence duplication levels.
- Examined adapter content.
- Selected five metrics for the first version of the automated QC pipeline.

### Metrics selected

1. Per-base sequence quality
2. Per-sequence quality scores
3. Per-sequence GC content
4. Sequence duplication levels
5. Adapter content

### What I learned

- FastQC provides multiple complementary indicators of sequencing quality.
- A QC metric should not necessarily be interpreted as simply good or bad without considering the biological context.
- Adapter contamination and sequencing quality can identify potential issues before downstream analysis.
- QC thresholds can potentially be converted into transparent computational rules.

### Design decision

The pipeline will initially use a rule-based QC system rather than machine learning. Each selected metric will be compared against predefined thresholds and assigned a PASS, WARNING or FAIL status.

### Next steps

- Determine appropriate thresholds for the selected QC metrics.
- Investigate how FastQC stores these results in machine-readable files.
- Plan how Python can automatically extract the metrics.

## Day 3 — QC Metrics and Threshold Design

**Date:** 7 October 2026

### Today's goals

- Select the quality-control metrics to be used in the automated pipeline.
- Understand how thresholds can be used to classify sequencing quality.
- Design an initial transparent PASS/WARNING/FAIL rule set.
- Consider the limitations of applying fixed thresholds to biological data.

### Selected QC metrics

The initial pipeline will focus on five metrics:

1. Per-base sequence quality
2. Per-sequence quality scores
3. Per-sequence GC content
4. Sequence duplication levels
5. Adapter content

### Initial QC rules

| Metric | PASS | WARNING | FAIL |
|---|---|---|---|
| Per-base sequence quality | Mean quality ≥ Q30 | Q20–Q29 | < Q20 |
| Low-quality reads | < 5% | 5–10% | > 10% |
| GC content | FastQC PASS | FastQC WARNING | FastQC FAIL |
| Sequence duplication | FastQC PASS | FastQC WARNING | FastQC FAIL |
| Adapter content | < 5% | 5–10% | > 10% |

### Design considerations

Not all sequencing QC metrics can be interpreted using a single universal numerical threshold. For example, GC-content distributions depend on the biological sample and sequencing context. Therefore, the initial prototype will use FastQC's interpretation for GC content and sequence duplication while using explicit numerical rules for selected metrics.

The thresholds are intended as transparent prototype rules for this project and are not clinical laboratory acceptance criteria.

### What I learned

- QC thresholds need to be interpreted in the context of the sequencing assay and biological sample.
- Some metrics are more suitable for direct numerical thresholding than others.
- A transparent rule-based approach makes the automated QC system easier to understand and explain.
- FastQC can provide an established baseline for interpreting several QC metrics.

### Next steps

- Investigate the machine-readable files generated by FastQC.
- Determine which files contain the selected QC metrics.
- Plan how Python can automatically extract the required values.
