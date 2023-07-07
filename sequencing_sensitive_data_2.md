## Sequencing Sensitive Data


NGS sequences derived from living persons can contain sensitive personal data subjected to GDPR and Danish National Data protection law, therefore your sequencing project will need safe handling/storage procedures suited for handling sensitive personal data. The project owner (typically the PI) needs to obtain a permission from your local Data Protection Agency and consent from the study subjects to store the data on special repositories. You can use [EMBL-EBI submission wizard](https://www.ebi.ac.uk/submission/) to understand where your data should be uploaded for publication.

As the project owner, you are responsible for the proper handling of the data. If you need sequencing as part of your project, we need to receive a sequencing request from you, which gives the frame around the task we are asked to perform for this project (timeframe, safe storage to copy the data to, etc.).

We provide here a template of the email we would like to receive from the project owner for each given project including personal data. If there is anything to addjust for your project, please let us know.


**Template email to send to genomics@sund.ku.dk**
 
```
Request to process data 
 
Research Project Owner _[FULL NAME]_ would like the Genomics Platform to sequence the various pools placed in the Genomics Platform freezer - and including sensitive personal data from patients - during the timeframe of _[01-07-2023]_ to _[31-12-2025]_ in order to create sequencing files including BCL images, as well as fastq, fastqc and multiQC files describing sequencing reads as part of the research project. 
 
The sequencing data mentioned above will be generated on one of the sequencers of the Genomics Platform and copied on the Genomics Platform General Sensivite SIF project for internal handling.

To deliver the task, the data will be copied on the following infrastructure - which is owned by the research project owner and appropriate for the project requirements: _[S-drive / SIF-project]_. 

At the latest by the end of the timeframe mentioned above, the sequencing pool will be trashed and the sequencing data will be deleted from the sequencer. 
 
The technical data related to the run (i.e. the sequencing folder without the bcl and fastq files) - which do not include personal data - can be kept on the Genomics Platform N-drives for technical meta-analyses and overall performance of the Genomics Platform. 
 
Contact person for this project is _[email@sund.ku.dk]_.
``` 

### Our practical workflow

For sensitive data projects, we will 
   * generate raw sequencing data on the sequencer and sync it on the sequencer itself while running (for other runs, we sync the data onto a N-drive while sequencing, but this is not allowed for sensitive data).
   * make a copy on our general SIF project, where only platform staff has access, for internal handling of the data
   * trash any remaining of the physical sample right after sequencing (we suggest you keep a backup in your lab if we need to resequence)

For sharing the data with you, we need you to indicate on which location we can transfer the data, e.g.:
   * Your project-specific S-drive, to which we need access
   * You project on [SIF](https://sif.ku.dk) (e.g. ERDA solution for sensitive data), to which we need access



Go back to the [Genomics Platform home](https://sundgenomics.github.io)
