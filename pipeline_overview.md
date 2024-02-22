
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

 **nf-core** pipelines offered by Genomics Platform
 - NF-CHIP ([nf-core/chipseq](https://nf-co.re/chipseq/2.0.0))
 - NF-CUTANDRUN ([nf-core/cutandrun](https://nf-co.re/cutandrun/3.2.2))
 - NF-METHYL ([nf-core/methylseq](https://nf-co.re/methylseq/2.6.0))
 - NF-RNA ([nf-cpre/rnaseq](https://nf-co.re/rnaseq/3.14.0))

### ATAC

ATAC pipeline aligns reads in .fastq to a specified reference genome, removes chrM and blacklisted regions for mouse. Spike-in option is not built in by default, but alignment can be done on a spike-in genome separately.

- Inputs: .fastq.gz files, a reference genome
- Options: paired-end only
- Outputs: indexed, sorted .bam files with chrM removed, .bw files
- Software used: bowtie2, samtools, picard, multiQC, bedtools

### CELL-RANGER

CELL-RANGER pipeline uses cellranger v.7.1.0 to demultiplex, count and aggregate the reads. Depending on library design (with or without cell hashing), further `cellranger count` + `cellranger aggr` or `cellranger multi` is used to create count matrixes for downstream analysis in Loupe browser, Seurat, etc. By default, the pipeline uses the [pre-built reference transcriptome by 10X](https://www.10xgenomics.com/support/software/cell-ranger/latest/analysis/inputs/cr-inputs-overview) for mouse and human.

### CHIP-CHOR-SCAR

CHORseq pipeline aligns reads in .fastq.gz to a specified reference genome, using dm6 as spike-in genome.This pipeline is used to align reads for CHIP and CHOR assays. 
This pipeline can handle UMIs. 

- Inputs: .fastq files, a reference genome  
- Options: single-end, paired-end, with and without spike-in
- Outputs: indexed, sorted .bam files  
- Software used: bowtie2, samtools, picard, multiQC, umi_tools, custom scripts  

![CHOR pipeline](/images/f03_CHOR.pdf)

### CRISPR




### CRISPRESSO2





### CUTRUN-CUTTAG

CUTRUN-CUTTAG pipeline is derived from the ATAC pipeline to handle reads produced by CUT&Run and Cut&Tag assays.

- Inputs: .fastq.gz files, a reference genome
- Options: paired-end only
- Outputs: indexed, sorted .bam files, .bw files
- Software used: bowtie2, samtools, picard, multiQC, bedtools, custom scripts


### FASTQ

Demultiplexing pipeline converts raw images (.bcl) into .fastq.gz files according to samplesheet provided by the user. Please find the most updated samplesheets [here](/demux.md)
- Inputs: raw .bcl files and a sample sheet  
- Outputs: .fastq files, multiQC report  
- Software used: bcl2fasta, multiQC  

![demux pipeline](/images/f01_demultiplex.pdf)

### RNA

RNAseq pipeline aligns reads in .fastq to a specified reference genome
- Inputs: .fastq.gz files
- Outputs: indexed, sorted .bam files, read counts in .tsv format  
- Software used: STAR, multiQC  

![RNA pipeline](/images/f02_RNAseq.pdf)


### RAW

If you select RAW option, we will give you access to the run folder containing raw images (.bcl), so you can demultiplex the reads yourself. 


### NF-CORE PIPELINES USED AT GENOMICS PLATFORM

Apart from maintaining in-house pipelines, Genomics Platform can run some [nf-core](https://nf-co.re/) pipelines if the user requests it:

 - NF-CHIP ([nf-core/chipseq](https://nf-co.re/chipseq/2.0.0))
 - NF-CUTANDRUN ([nf-core/cutandrun](https://nf-co.re/cutandrun/3.2.2))
 - NF-METHYL ([nf-core/methylseq](https://nf-co.re/methylseq/2.6.0))
 - NF-RNA ([nf-cpre/rnaseq](https://nf-co.re/rnaseq/3.14.0))

We also highly recommend to try running these pipelines by themselves and are happy to provide support and training for running these pipeliens whenever a user requests help. 

A dangpu-specific profile available for [nf-core/configs](https://github.com/nf-core/configs). 
Please see development (aka most uopdated) guidelines for nf-core pipelines [here](https://github.com/AdrijaK/configs/blob/master/docs/ku_sund_dangpu.md).


### RUNNING OTHER COMMUNITY PIPELINES

You can always ask for help to run other community-maintained pipelines that are within nf-core and SnakePipes platforms. To run snakepipes on dangpu server run the following command and follow the instructions. 

```bash
module load miniconda/latest snakePipes/2.5.4
```

The snakePipes workflows call SLURM jobs by default, so you do not need to run snakePipes workflows as slurm jobs. You can specify max CPUs with an option `-j`. Remember to not exceed the maximum allowed number of CPUs on dangpu during the work hours. You can read more on how to use dangpu server [here](https://sgn102.pages.ku.dk/a-not-long-tour-of-dangpu/)



### AVAILABLE REFERENCE GENOMES

refgenie reference genome manager is available for accessing for pre-built reference genomes on dangpu server:

```bash
# load modules
module load dangpu_libs python/3.7.13 refgenie/0.12.1

# list genomes
refgenie list -g  GRCh38_ensembl

# find a path to the file of interest
# syntax: refgenie seek <genome>/<asset>:<tags>
refgenie seek  GRCh38_ensembl/bowtie2_index
refgenie seek  GRCh38_ensembl/blacklist:CUTANDRUN
```

[refgenie documentation](http://refgenie.databio.org/en/latest/)  
[more guidelines for dangpu server](https://sgn102.pages.ku.dk/a-not-long-tour-of-dangpu/)  

Go back to the [Genomics Platform home](https://sundgenomics.github.io)

