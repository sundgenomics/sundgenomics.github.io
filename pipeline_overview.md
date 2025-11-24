
## Overview of pipelines offered by Genomics Platform

The following pipelines can be selected for the Genomics Platform to run:

 **nf-core** pipelines offered by Genomics Platform
 - NF-CHIP ([nf-core/chipseq](https://nf-co.re/chipseq/2.0.0))
 - NF-CUTANDRUN ([nf-core/cutandrun](https://nf-co.re/cutandrun/3.2.2))
 - NF-METHYL ([nf-core/methylseq](https://nf-co.re/methylseq/2.6.0))
 - NF-RNA ([nf-core/rnaseq](https://nf-co.re/rnaseq/3.14.0))
 - NF-ATAC ([nf-core/atacseq](https://nf-co.re/atacseq/2.1.2/)

**in-house** pipelines offered by Genomics Platform:
 - ATAC 
 - CELL-RANGER
 - CHIP-CHOR-SCAR
 - CRISPRESSO2
 - CUTRUN-CUTTAG
 - FASTQ
 - MAGECK
 - MAGECK-DRUGZ-BAGEL
 - MAGECK-BE
 - MAGECK-BEAN
 - RAW
 - RNA (deprecated)

**We ALWAYS include a copy of the script we used to run the pipeline when we share the pipeline output with the user to make sure the results are reproducible. You can find details on how the pipeline was run as .sbatch file inside the pipeline folder.**

---

### NF-CORE PIPELINES

Genomics Platform can also run selected [nf-core](https://nf-co.re/) pipelines:

**NF-CHIP** [https://nf-co.re/chipseq/2.0.0](https://nf-co.re/chipseq/2.0.0)  
**NF-CUTANDRUN** [https://nf-co.re/cutandrun/3.2.2](https://nf-co.re/cutandrun/3.2.2)  
**NF-METHYL** [https://nf-co.re/methylseq/2.6.0](https://nf-co.re/methylseq/2.6.0)  
**NF-RNA** [https://nf-co.re/rnaseq/3.14.0](https://nf-co.re/rnaseq/3.14.0)  
**NF-ATAC** [https://nf-co.re/atacseq/2.1.2/](https://nf-co.re/atacseq/2.1.2/)  

- genomics platform uses a standard set of parameters when running nf-core pipelines. If the user needs spcific parameters, this should be discussed with the genomics platform before the libraries are submitted!

- We **highly recommend** users try running these pipelines themselves: we provide **support and training** during data drop-in on Wednesdays 13:00-14:00.  

- Please read the **pipeline usage guidelines**: (nf-core/configs - ku_sund_danhead](https://nf-co.re/configs/ku_sund_danhead/)

---

### ATAC

ATAC pipeline aligns reads in .fastq to a specified reference genome, and removes mitochondrial reads. Spike-in option is not built in by default, but alignment can be done on a spike-in genome separately.

- Inputs: .fastq.gz files, a reference genome
- Options: paired-end only
- Outputs: indexed, sorted .bam files with chrM removed, .bw files
- Software used: bowtie2, samtools, picard, multiQC, bedtools

---

### CELL-RANGER

CELL-RANGER pipeline uses cellranger v.7.1.0 to demultiplex, count and aggregate the reads. Depending on library design (with or without cell hashing), further `cellranger count` + `cellranger aggr` or `cellranger multi` is used to create count matrixes for downstream analysis in Loupe browser, Seurat, etc. By default, the pipeline uses the [pre-built reference transcriptome by 10X](https://www.10xgenomics.com/support/software/cell-ranger/latest/analysis/inputs/cr-inputs-overview) for mouse and human.

---

### CHIP-CHOR-SCAR

CHIP-CHOR-SCAR  pipeline aligns reads in .fastq.gz to a specified reference genome, using dm6 as the spike-in genome. This pipeline is used to align reads for CHIP and CHOR assays. This pipeline can handle UMIs. 

- Inputs: .fastq files, a reference genome  
- Options: single-end, paired-end, with and without spike-in
- Outputs: indexed, sorted .bam files  
- Software used: bowtie2, samtools, picard, multiQC, umi_tools, custom scripts  

---

### CRISPRESSO2

CRISPRESSO2 pipeline is used for amplicon submissions and described [here](http://crispresso.pinellolab.org/submission).

---

### CUTRUN-CUTTAG

CUTRUN-CUTTAG pipeline is derived from the ATAC pipeline to handle reads produced by CUT&Run and Cut&Tag assays.

- Inputs: .fastq.gz files, a reference genome
- Options: paired-end only
- Outputs: indexed, sorted .bam files, .bw files
- Software used: bowtie2, samtools, picard, multiQC, bedtools, custom scripts

---

### FASTQ

FASTQ pipeline demultiplexes raw images (.bcl) into .fastq.gz files according to samplesheet provided by the user. It can handle UMIs. 

Please find the most updated samplesheets [here](/demux.md)
- Inputs: raw .bcl files and a sample sheet  
- Outputs: .fastq files, multiQC report, md5sums for fastq files
- Software used: bcl2fasta, multiQC

---

### MAGECK

This pipeline was developed with Emil Hertz (CPR) and tailored for specific CRISPR primers following Durocher's lab protocol. If unaware, please ask us about it. The pipeline trims the reads (taking into account the staggers if present) and then run Mageck on the trimmed fastq with the library file indicated in the samplesheet.

---

### MAGECK-BE and MAGECK-BEAN

For CRISPR_reporter_library submissions, we typically run Mageck 3 times as follows (MAGECK-BE):
  * guide on R1
  * rev-compl of guide on R2
  * insert on R1

In addition, it can be useful to run [BEAN](https://pinellolab.github.io/crispr-bean/). We have investigated that tool and initially created MAGECK-BEAN pipeline to apply both methods. However, it is not clear at this point how to run BEAN in a routine way, so MAGECK-BEAN is not used at the moment, but we use instead MAGECK-BE, which only focused on MAGECK.

---

### MAGECK-DRUGZ-BAGEL

This pipeline starts with the Mageck pipeline explained above to compute the raw count matrix. After that, we run DrugZ on the raw counts. Also, we compute a normalised count matrix and run Bagel. For all these steps, we need you to email us the details of the experimental design amd which exact comparisons you need.

---

### RNA (deprecated)

**ATTENTION: this pipeline is deprecated. We recommend selecting nf-core/rnaseq pipeline instead (NF-RNA). PLease contact us if you need this pipeline for finishing old projects**

RNAseq pipeline aligns reads in .fastq to a specified reference genome using STAR. We currently offer running this pipeline for projects that need wrapping-up, but for the new projects we recommend using NF-RNA pipeline. 

- Inputs: .fastq.gz files
- Outputs: indexed, sorted .bam files, read counts in .tsv format  
- Software used: STAR, multiQC

---

### RAW

If you select RAW option, we will give you access to the run folder containing raw images (.bcl), so you can demultiplex the reads yourself. 

---

### RUNNING OTHER COMMUNITY PIPELINES

You can always ask for help to run other community-maintained pipelines that are within nf-core and SnakePipes platforms. To run snakepipes on dangpu server run the following command and follow the instructions. 

```bash
module load miniconda/latest snakePipes/2.5.4
```

The snakePipes workflows call SLURM jobs by default, so you do not need to run snakePipes workflows as slurm jobs. You can specify max CPUs with an option `-j`. Remember to not exceed the maximum allowed number of CPUs on DANHEAD during the work hours. [You can read more on how to use DANHEAD HPC here.](https://sgn102.pages.ku.dk/a-not-long-tour-of-dan-system/)

---

### AVAILABLE REFERENCE GENOMES

refgenie reference genome manager is available for accessing for pre-built reference genomes on dangpu server: [more info here](/refgenie.md)

---

Go back to the [Genomics Platform home](https://sundgenomics.github.io)

