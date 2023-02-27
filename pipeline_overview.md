
## Overview of pipelines offered by Genomics Platform

### DEMULTIPLEX

Demultiplexing pipeline converts raw images (.bcl) into .fastq files according to samplesheet provided by the user. 
- Inputs: raw .bcl files and a sample sheet  
- Outputs: .fastq files, multiQC report  
- Software used: bcl2fasta, multiQC  

![demux pipeline](/images/f01_demultiplex.pdf)
### RNAseq

RNAseq pipeline aligns reads in .fastq to a specified reference genome
- Inputs: .fastq files, a reference genome  
- Outputs: indexed, sorted .bam files, read counts in .tsv format  
- Software used: STAR, multiQC  

![RNA pipeline](/images/f02_RNAseq.pdf)

### CHORseq

CHORseq pipeline aligns reads in .fastq to a specified reference genome, using dm-6 as spike-in
- Inputs: .fastq files, a reference genome  
- Outputs: indexed, sorted .bam files  
- Software used: bowtie2, samtools, picard, multiQC, custom scripts  

![CHOR pipeline](/images/f03_CHOR.pdf)

### ATACseq

TBA

### CHIPseq

TBA

### COMMUNITY PIPELINES

Apart from maintaining in-house pipelines, Genomics Platform supports use of [snakePipes](https://snakepipes.readthedocs.io/en/latest/) and [nf-core](https://nf-co.re/) pipelines. 

#### SnakePipes

#### nf-core
There is a [dangpu-specific profile](https://github.com/nf-core/configs/blob/master/docs/ku_sund_dangpu.md) available for nf-core pipelines. 
Please see development (aka most uopdated) guidelines at https://github.com/AdrijaK/configs.

