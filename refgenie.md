# Using reference genomes with refgenie

Reference genomes used in genomics pipelines can be accessed via [refgenie](http://refgenie.databio.org/en/latest/). 

[Please refer to DANGPU user guide for more details.](https://sgn102.pages.ku.dk/a-not-long-tour-of-dangpu/#reference-genomes-on-dangpu) 

In short, you can find available reference genomes like this:

```bash
module load python/3.8.16 refgenie/0.12.1a
refgenie list
```

which will output a list of available genomes.
```bash
                                                       Local refgenie assets                                                       
                                        Server subscriptions: http://refgenomes.databio.org                                        
┏━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃ genome              ┃ assets                                                                                                    ┃
┡━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┩
│ GRCh38_ensembl      │ fasta, ensembl_gtf, gencode_gtf, blacklist, star_index, bowtie2_index, bismark_bt2_index, 10x_index       │
│ hg38_refgenie, hg38 │ fasta, gencode_gtf, ensembl_gtf, bwa_index, bowtie2_index, star_index, hisat2_index,                      │
│                     │ cellranger_reference, bismark_bt2_index, fasta_txome, salmon_sa_index                                     │
│ GRCm39_ensembl      │ fasta, ensembl_gtf, bowtie2_index, star_index, bismark_bt2_index, 10x_index, blacklist                    │
│ dm6_ensembl         │ fasta, bowtie2_index                                                                                      │
│ GRCh38_dm6          │ fasta, bowtie2_index                                                                                      │
│ GRCm39_dm6          │ fasta, bowtie2_index                                                                                      │
│ GRCh38_legacy       │ fasta, gencode_gtf, blacklist, gtf_TE, star_index, bowtie2_index, bismark_bt2_index, 10x_index            │
│ mm10_legacy         │ fasta, gencode_gtf, blacklist, star_index, bowtie2_index, bismark_bt2_index, 10x_index                    │
│ dm6_FlyBase         │ fasta, flybase_gtf, star_index, bowtie2_index, bismark_bt2_index                                          │
│ puc19               │ fasta, bismark_bt2_index                                                                                  │
│ lambda              │ fasta, bismark_bt2_index                                                                                  │
│ Spombe_h90          │ fasta, bowtie2_index                                                                                      │
│ Ecoli               │ fasta, bowtie2_index                                                                                      │
│ sacCer3             │ fasta, ncbi_gff, star_index, bowtie2_index                                                                │
└─────────────────────┴───────────────────────────────────────────────────────────────────────────────────────────────────────────┘
```

You can further find contents of each reference genome using `list -g` option:
```bash
refgenie list -g GRCh38_ensembl
```

which gives you the information on available assets for the reference genome of interest:
```bash
                                         Local refgenie assets                                         
                          Server subscriptions: http://refgenomes.databio.org                          
┏━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━┓
┃ genome         ┃ asset (seek_keys)                                              ┃ tags              ┃
┡━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━┩
│ GRCh38_ensembl │ fasta (fasta, fai, chrom_sizes, dir)                           │ release_111       │
│ GRCh38_ensembl │ ensembl_gtf (ensembl_gtf, ensembl_tss, ensembl_gene_body, dir) │ release_111       │
│ GRCh38_ensembl │ gencode_gtf (gencode_gtf, dir)                                 │ release_45        │
│ GRCh38_ensembl │ blacklist (blacklist, dir)                                     │ CUTANDRUN, ENCODE │
│ GRCh38_ensembl │ star_index (star_index, dir)                                   │ 2.7.11b           │
│ GRCh38_ensembl │ bowtie2_index (bowtie2_index, dir)                             │ 2.5.3             │
│ GRCh38_ensembl │ bismark_bt2_index (bismark_bt2_index, dir)                     │ 0.24.2            │
│ GRCh38_ensembl │ 10x_index (10x_index, dir, filtered_gtf)                       │ 7.2.0             │
└────────────────┴────────────────────────────────────────────────────────────────┴───────────────────┘
```

finally, you can find a path to a specific asset as `<genome>/<asset>:<tag>`
```bash
refgenie seek GRCh38_ensembl/blacklist:CUTANDRUN
```

which gives you a path to the asset file:
```bash
/maps/projects/dan1/data/RefGenomes_reNEW/alias/GRCh38_ensembl/blacklist/CUTANDRUN/GRCh38_ensembl_blacklist.bed.gz
```

## Reference genome options for human (hg)

For human reference genome there are several options:  

**GRCh38_ensembl** - the most updated reference genome that we suggest for new projects starting from 2024 and on. We currently use this as our default reference genome for human.  
  
**GRCh38_legacy** - The human reference genome the Genomics Platform used 2017-2023.  
  
**GRCh38_dm6** - hybrid genome between GRCh38_ensembl and dm6_ensembl. This can be used for alignments when you have used spike-in from the fly. This reference contains only fasta and bowtie2 index.  
  
**GRCh38_refgenie** (same as GRCh38) - the reference genome pulled from refgenie. Genomics Platform does not use this reference but it is available for users. Please note that if you run nf-core pipelines and use GRCh38 as reference genome, it will use GRCh38 from [AWS_iGenomes](https://ewels.github.io/AWS-iGenomes/) reference genome instead of refgenie local list.  

## Reference genome options for mouse (mm)

For mouse reference genome there are also several options:  
  
**GRCm39_ensembl** - the newest reference genome that we recommend for new projects starting from 2024 and on. This genome is the default reference genome for running Genomics Platform pipelines.  
  
**mm10_legacy** - This is the mouse reference genome we used 2017-2023.  
  
**GRCm39_dm6** - hybrid genome between GRCm39_ensembl and dm6_ensembl. This can be used for alignments when you have used spike-in from the fly.  


## Other reference genomes
There are various spike-in genomes included in refgenie:  
dm6_ensembl  
dm6_FlyBase  
puc19  
lambda  
Spombe_h90  
Ecoli  
sacCer3  

## Genomes in detail
Below you can find more detailed description of some of the main genomes.

### GRCh38_ensembl

```bash
refgenie list -g  GRCh38_ensembl
```

```bash
                                         Local refgenie assets                                         
                          Server subscriptions: http://refgenomes.databio.org                          
┏━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━┓
┃ genome         ┃ asset (seek_keys)                                              ┃ tags              ┃
┡━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━┩
│ GRCh38_ensembl │ fasta (fasta, fai, chrom_sizes, dir)                           │ release_111       │
│ GRCh38_ensembl │ ensembl_gtf (ensembl_gtf, ensembl_tss, ensembl_gene_body, dir) │ release_111       │
│ GRCh38_ensembl │ gencode_gtf (gencode_gtf, dir)                                 │ release_45        │
│ GRCh38_ensembl │ blacklist (blacklist, dir)                                     │ CUTANDRUN, ENCODE │
│ GRCh38_ensembl │ star_index (star_index, dir)                                   │ 2.7.11b           │
│ GRCh38_ensembl │ bowtie2_index (bowtie2_index, dir)                             │ 2.5.3             │
│ GRCh38_ensembl │ bismark_bt2_index (bismark_bt2_index, dir)                     │ 0.24.2            │
│ GRCh38_ensembl │ 10x_index (10x_index, dir, filtered_gtf)                       │ 7.2.0             │
└────────────────┴────────────────────────────────────────────────────────────────┴───────────────────┘
```

#### Characteristics
This genome genome uses `fasta` (GRCh38.p14 primary assembly from soft masked genome) and `ensembl_gtf` (Ensembl release 111) to generate `star_index` (using STAR 2.7.11b) `bowtie2_index` (using bowtie2 v.2.5.3) `bismark_bt2_index` (using bismark v.0.24.2) and `10x_index` for GEX (using CellRanger v.7.2.0).

```bash
VERSION=111
wget -L http://ftp.ensembl.org/pub/release-${VERSION}/fasta/homo_sapiens/dna/Homo_sapiens.GRCh38.dna_sm.primary_assembly.fa.gz
wget -L http://ftp.ensembl.org/pub/release-${VERSION}/gtf/homo_sapiens/Homo_sapiens.GRCh38.${VERSION}.gtf.gz
```

#### Additional files
`gencode_gtf`: Gencode release 45  
`blacklist` files contain regions prone to misalignment or bias in genomic analysis. 
`blacklist:ENCODE` is sourced from [ENCODE project](https://github.com/Boyle-Lab/Blacklist/blob/master/lists/hg38-blacklist.v2.bed.gz) for use with ATAC/ChIP-seq and  
`blacklist:CUTANDRUN` is sourced from [Nordin et al. 2023](https://genomebiology.biomedcentral.com/articles/10.1186/s13059-023-03027-3) for use with CUT&RUN.  

#### Additional info
Chromosome names: 1, 2, 3, ... , MT, X, Y
Effective genome sizes can be found in [deeptools documentation](https://deeptools.readthedocs.io/en/develop/content/feature/effectiveGenomeSize.html) 


### GRCm39_ensembl

```bash
refgenie list -g  GRCm39_ensembl
```

```bash
┏━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃ genome         ┃ asset (seek_keys)                                              ┃ tags                     ┃
┡━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━┩
│ GRCm39_ensembl │ fasta (fasta, fai, chrom_sizes, dir)                           │ release_111              │
│ GRCm39_ensembl │ ensembl_gtf (ensembl_gtf, ensembl_tss, ensembl_gene_body, dir) │ release_111              │
│ GRCm39_ensembl │ bowtie2_index (bowtie2_index, dir)                             │ 2.5.3                    │
│ GRCm39_ensembl │ star_index (star_index, dir)                                   │ 2.7.11b                  │
│ GRCm39_ensembl │ bismark_bt2_index (bismark_bt2_index, dir)                     │ 0.24.2                   │
│ GRCm39_ensembl │ 10x_index (10x_index, dir, filtered_gtf)                       │ 7.2.0                    │
│ GRCm39_ensembl │ blacklist (blacklist, dir)                                     │ CUTANDRUN, EXCLUDERANGES │
└────────────────┴────────────────────────────────────────────────────────────────┴──────────────────────────┘
```

#### Characteristics
This genome references use `fasta` (GRCm39 primary assembly) and `ensembl_gtf` (Ensembl release 111) to build `star_index` for STAR v.2.7.11b, `bowtie2_index` for bowtie2 v.2.5.3, `bismark_bt2_index` for Bismark v.0.24.2. and `10x_index` for Cellranger v.7.2.0.  

```bash
VERSION=111
wget -L http://ftp.ensembl.org/pub/release-${VERSION}/fasta/mus_musculus/dna/Mus_musculus.GRCm39.dna_sm.primary_assembly.fa.gz
wget -L http://ftp.ensembl.org/pub/release-${VERSION}/gtf/mus_musculus/Mus_musculus.GRCm39.${VERSION}.gtf.gz
```

#### Additional files
`blacklist` files are included:  
`blacklist:EXCLUDERANGES` from [Ogata et al. 2023](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC10126321/) for use with ChIPseq and ATACseq assays and  
`blacklist:CUTANDRUN` from [Nordin et al. 2023](https://genomebiology.biomedcentral.com/articles/10.1186/s13059-023-03027-3) for use with CUT&RUN and CUT&TAG assays. 

#### Additional info
Chromosome names: 1, 2, 3, ... , MT, X, Y  
Effective genome sizes can be found in [deeptools documentation](https://deeptools.readthedocs.io/en/develop/content/feature/effectiveGenomeSize.html) 

### GRCh38_legacy
```bash
refgenie list -g GRCh38_legacy
```

```bash
                               Local refgenie assets                                
                Server subscriptions: http://refgenomes.databio.org                 
┏━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━┓
┃ genome        ┃ asset (seek_keys)                                      ┃ tags    ┃
┡━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━┩
│ GRCh38_legacy │ fasta (fasta, fai, chrom_sizes, hg38_chrom_sizes, dir) │ default │
│ GRCh38_legacy │ gencode_gtf (gencode_gtf, dir)                         │ default │
│ GRCh38_legacy │ blacklist (blacklist, dir)                             │ ENCODE  │
│ GRCh38_legacy │ gtf_TE (gtf_TE, dir)                                   │ default │
│ GRCh38_legacy │ star_index (star_index, dir)                           │ 2.7.2d  │
│ GRCh38_legacy │ bowtie2_index (bowtie2_index, dir)                     │ default │
│ GRCh38_legacy │ bismark_bt2_index (bismark_bt2_index, dir)             │ 0.22.3  │
│ GRCh38_legacy │ 10x_index (10x_index, dir)                             │ default │
└───────────────┴────────────────────────────────────────────────────────┴─────────┘
```

#### Characteristics
For GRCh38_legacy reference, `fasta` (Encode fasta GRCh38.p13) and `gencode_gtf` (from gencode.v32) were used to generate `star_index` using STAR v.2.7.2d, `bowtie2_index` using bowtie2 v2.3.4.1, `bismark_bt2_index` using bismark v0.22.3, `gtf_TE` for using with TETranscripts.  

#### Additional files
`10x_index`: 10x index for GEX, issued by 10x in 2020 as refdata-gex-GRCh38-2020-A  
`blacklist`: ENCODE blacklist sourced from [nf-core/atac assets](https://github.com/nf-core/atacseq/tree/master/assets/blacklists/v2.0)

#### Additional info
Chromosome naming: chr1, chr2, ... chrM, chrX, chrY.
Effective genome sizes can be found in [deeptools documentation](https://deeptools.readthedocs.io/en/develop/content/feature/effectiveGenomeSize.html)  

### mm10_legacy

```bash
┏━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━┓
┃ genome      ┃ asset (seek_keys)                          ┃ tags              ┃
┡━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━┩
│ mm10_legacy │ fasta (fasta, fai, chrom_sizes, dir)       │ default           │
│ mm10_legacy │ gencode_gtf (gencode_gtf, dir)             │ default           │
│ mm10_legacy │ blacklist (blacklist, dir)                 │ ENCODE, GUAVA     │
│ mm10_legacy │ star_index (star_index, dir)               │ 2.7.2d            │
│ mm10_legacy │ bowtie2_index (bowtie2_index, dir)         │ default           │
│ mm10_legacy │ bismark_bt2_index (bismark_bt2_index, dir) │ 0.22.3            │
│ mm10_legacy │ 10x_index (10x_index, dir)                 │ GEX, GEX_GFP, ARC │
└─────────────┴────────────────────────────────────────────┴───────────────────┘
```

#### Characteristics 
mm10_legacy genome references use `fasta` (GRCm38.p5 primary_assembly) and `gencode_gtf` (gencode vM15) to generate `star_index` for STAR v.2.7.2d , `bowtie2_index` and `bismark_bt2_index` for Bismark v.0.22.3.  

#### Additional files
`blacklist` files are included:
`blacklist:ENCODE` from [ENCODE](https://github.com/Boyle-Lab/Blacklist/blob/master/lists/mm10-blacklist.v2.bed.gz) and  
`blacklist:GUAVA` from [GUAVA](https://github.com/MayurDivate/GUAVA/blob/master/lib/blacklists/JDB_blacklist.mm10.bed)  
`10x_index` files (issued by 10x in 2020): `10_index:GEX` for gene expression profiling, `10x_index:ARC` for single cell ATAC. For internal use we have also generated , `10x_index:GEX_GFP` for gene expression profiling with GFP reference included.  

#### Additional info
Chromosome naming: chr1, chr2, ... chrM, chrX, chrY.
Effective genome sizes can be found in [deeptools documentation](https://deeptools.readthedocs.io/en/develop/content/feature/effectiveGenomeSize.html) 
