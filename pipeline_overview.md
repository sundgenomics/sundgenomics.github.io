
## Overview of pipelines offered by Genomics Platform

The following pipelines can be selected for the Genomics Platform to run:

**in-house** pipelines offered by Genomics Platform:
 - ATAC 
 - CELL-RANGER
 - CHIP-CHOR-SCAR
 - CRISPR
 - CRISPRESSO2
 - CUTRUN-CUTTAG
 - FASTQ
 - RAW

 nf-core pipelines offered by Genomics Platform
 - NF-CHIP
 - NF-CUTANDRUN
 - NF-METHYL
 - NF-RNA

### ATAC

ATAC pipeline aligns reads in .fastq to a specified reference genome, removes chrM and blacklisted regions for mouse. Spike-in option is not built in by default, but alignment can be done on spike-in genome separately.

- Inputs: .fastq.gz files, a reference genome
- Options: paired-end only
- Outputs: indexed, sorted .bam files with chrM removed, .bw files
- Software used: bowtie2, samtools, picard, multiQC, bedtools

### CELL-RANGER

...

### CHIP-CHOR-SCAR

CHORseq pipeline aligns reads in .fastq to a specified reference genome, using dm-6 as spike-in genome.This pipeline is used to align reads for CHIP and CHOR assays. 
This pipeline can handle UMIs. 

- Inputs: .fastq files, a reference genome  
- Options: single-end, paired-end, with and without spike-in
- Outputs: indexed, sorted .bam files  
- Software used: bowtie2, samtools, picard, multiQC, umi_tools, custom scripts  

![CHOR pipeline](/images/f03_CHOR.pdf)

### CRISPR




### CRISPRESSO2




### CUTRUN-CUTTAG

This pipeline is derived from the ATAC pipeline to handle reads produced by CUT'n'Run and Cut&Tag assays. 

- Inputs: .fastq.gz files, a reference genome
- Options: paired-end only
- Outputs: indexed, sorted .bam files .bw files
- Software used: bowtie2, samtools, picard, multiQC, bedtools, custom scripts


### FASTQ

Demultiplexing pipeline converts raw images (.bcl) into .fastq files according to samplesheet provided by the user. 
- Inputs: raw .bcl files and a sample sheet  
- Outputs: .fastq files, multiQC report  
- Software used: bcl2fasta, multiQC  

![demux pipeline](/images/f01_demultiplex.pdf)

### RNA

RNAseq pipeline aligns reads in .fastq to a specified reference genome
- Inputs: .fastq files, a reference genome  
- Outputs: indexed, sorted .bam files, read counts in .tsv format  
- Software used: STAR, multiQC  

![RNA pipeline](/images/f02_RNAseq.pdf)


### RAW

If you select RAW option, we will give you access to the run folder containing raw images (.bcl), so you can demultiplex the reads yourself. 


## NF-CORE PIPELINES USED AT GENOMICS PLATFORM

Apart from maintaining in-house pipelines, Genomics Platform can run some [nf-core](https://nf-co.re/) pipelines if the user requests it. We also highly recommend to try running these pipelines by themselves and are happy to provide support and training for running these pipeliens whenever users request help. 

A dangpu-specific profile available for [nf-core/configs](https://github.com/nf-core/configs). 
Please see development (aka most uopdated) guidelines for nf-core pipelines [here](https://github.com/AdrijaK/configs/blob/master/docs/ku_sund_dangpu.md).


#### RUNNING OTHER COMMUNITY PIPELINES

You can always ask for help to run other community-maintained pipelines that are within nf-core and SnakePipes platforms. To run snakepipes on dangpu server run the following command and follow the instructions. 

```bash
module load miniconda/latest snakePipes/2.5.4
```

The snakePipes workflows call SLURM jobs by default, so you do not need to run snakePipes workflows as slurm jobs. You can specify max CPUs with an option `-j`. Remember to not exceed the maximum allowed number of CPUs on dangpu during the work hours. You can read more on how to use dangpu server [here](https://sgn102.pages.ku.dk/a-not-long-tour-of-dangpu/)



### AVAILABLE GENOMES

Genomics platform uses can use refgenie for pre-built reference genomes. 
```bash
module load dangpu_libs python/3.7.13 refgenie/0.12.1
```
[refgenie documentation](http://refgenie.databio.org/en/latest/)




Go back to the [Genomics Platform home](https://sundgenomics.github.io)

