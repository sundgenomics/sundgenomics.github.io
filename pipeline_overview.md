
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

CHORseq pipeline aligns reads in .fastq to a specified reference genome, using dm-6 as spike-in genome.
- Inputs: .fastq files, a reference genome  
- Options: single-end, paired-end, with and without spike-in
- Outputs: indexed, sorted .bam files  
- Software used: bowtie2, samtools, picard, multiQC, custom scripts  

![CHOR pipeline](/images/f03_CHOR.pdf)

### ATACseq

ATAC pipeline aligns reads in .fastq to a specified reference genome, removes chrM and blacklisted regions for mouse. Spike-in option is not built in by default, but alignment can be done on dm-6 genome separately.

- Inputs: .fastq.gz files, a reference genome
- Options: paired-end only
- Outputs: indexed, sorted .bam files with chrM removed, .bw files
- Software used: bowtie2, samtools, picard, multiQC, bedtools

### CHIPseq

- Inputs: .fastq.gz files, a reference genome
- Options: single-end
- Outputs: indexed, sorted .bam files with chrM removed. 
- Software used: bowtie2, samtools, picard, multiQC

### COMMUNITY PIPELINES

Apart from maintaining in-house pipelines, Genomics Platform supports use of [snakePipes](https://snakepipes.readthedocs.io/en/latest/) and [nf-core](https://nf-co.re/) pipelines. 

#### SnakePipes

To run snakepipes on dangpu server run the following command and follow the instructions. 

```bash
module load miniconda/latest snakePipes/2.5.4
```

#### nf-core
A dangpu-specific profile available for [nf-core/configs](https://github.com/nf-core/configs). 
Please see development (aka most uopdated) guidelines [here](https://github.com/AdrijaK/configs/blob/master/docs/ku_sund_dangpu.md).

### Common genomes

You can use refgenie for pre-built reference genomes. 
```bash
module load dangpu_libs python/3.7.13 refgenie/0.12.1
```

find available pre-built refgenie resources:
```bash
refgenie listr
```

find locally downloaded refgenie resources
```bash
refgenie seek mm10/bowtie2_index
```
[refgenie documentation](http://refgenie.databio.org/en/latest/)
