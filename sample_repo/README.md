# (Project Title) GEN711/811 Final Project

## (Group Members) By:
Niall, Zayn, Harry, Liam, Louis

## (Where your data comes from) Background

- title of paper
- authors
- Summary of original project
- what data are you using from paper (16s sanger sequencing, whole genome HiC, transcriptome 150bp illumina, etc)
- what is the goal of your project (e.g. to identify differences in microbiome composition, to identify genes associated with a specific phenotype, etc)

## Methods

- Where data is from
- what type of data is it (150bp illumina, 16s sanger sequencing, etc)
- where are you performing your analysis (RON, Premise, laptop, etc)
- what program did you use first (fastqc, trimmomatic, etc)
    - what that program did (trimmed reads, output statistics, etc)
        - a paragraph or two at most for each tool
    - what did that produce (fastq, bam, vcf, etc)
- what program did you use next (bowtie2, samtools, etc)
- write out whole pipeline ...
- how did you visualize your results (R, python,  qiime2 visualizer, etc)

### Example (Of a single tool)
#### FastQC
FastQC did a quality control check on the raw sequence fastq data. It produced a series of plots and statistics that assessed the quality of the data. The output of FastQC was an HTML report that included per-base quality scores, GC content, and adapter content.

#### Trimmomatic
...

## Findings
![plot](figures/venn.png)
- Label figure (Figure1)
- What kind of plot is it? (Venn Diagram)
- What does the plot show (the number of unique genes in each sample, the number of genes shared between samples)
- How did you create the plot (R, python, qiime2 visualizer, etc)
- What was the input to the plot (gene names + counts from bowtie2, etc)
- __figure caption formatting (not like the list above)__

__Do this for 2 figures__

## (References) Citations
Can be in any format, make sure it is consistent. I reccomend downloading [Zotero](https://libraryguides.unh.edu/zotero-durham/get-zotero) for all citation needs.
- Original Paper Citation
- All Tool Citations 

example
1. Nguyen, L.-T., Schmidt, H. A., von Haeseler, A. & Minh, B. Q. IQ-TREE: A Fast and Effective Stochastic Algorithm for Estimating Maximum-Likelihood Phylogenies. Molecular Biology and Evolution 32, 268–274 (2015).
2. Prjibelski, A., Antipov, D., Meleshko, D., Lapidus, A. & Korobeynikov, A. Using SPAdes De Novo Assembler. Current Protocols in Bioinformatics 70, e102 (2020).
