## Sequencing Sensitive Data


NGS sequences derived from living persons can contain sensitive personal data subjected to GDPR and Danish National Data protection law, therefore your sequencing project will need safe handling/storage procedures suited for handling sensitive personal data. The project owner (typically the PI) needs to obtain a permission from your local Data Protection Agency and consent from the study subjects to store the data on special repositories. You can use [EMBL-EBI submission wizard](https://www.ebi.ac.uk/submission/) to understand where your data should be uploaded for publication.

As the project owner, you are responsible for the proper handling of the data. If you need sequencing as part of your project, we need to receive a sequencing request from you, which gives the frame around the task we are asked to perform for this project (timeframe, safe storage to copy the data to, etc.).

We provide here a template of the email we would like to receive from the project owner for each given project including personal data. If there is anything to addjust for your project, please let us know.


**Template email to send to genomics@sund.ku.dk**
 
```
Request to process data for submission SUBXXX

Research Project Owner [FULL NAME] would like to notify the Genomics Platform that the direct sequencing submission [SUBXXX] contains sensitive patient material that will create sensitive data after sequencing: the sensitive data will be BCL images and fastq files.
 
The sequencing data for this run will be generated on a sequencer at the Genomics Platform and copied to the dangpu server within the sensitive and access-controlled dataset /datasets/renew_genomics_sdata-AUDIT for internal handling. 

To deliver the task, the data will be copied on the following infrastructure - which is owned by the research project owner and appropriate for the project requirements: [S-drive / SIF-project / S-dataset]. 

The library pool will be immediately discarded after sequencing and the sequencing data will be deleted from the sequencer after completing the data transfer to safe storage drive. 

The technical data related to the run (i.e. the sequencing folder without the bcl and fastq files) - which do not include personal data - can be kept on the Genomics Platform N-drives for technical meta-analyses and overall performance of the Genomics Platform. 

Contact person for this project is [email@sund.ku.dk].
``` 

### Our practical workflow

For sensitive data projects, we will 
   * generate raw sequencing data on the sequencer
   * sync it while running to our server dangpu sensitive dataset (/datasets/renew_genomics_sdata-AUDIT), where only platform staff has access, for internal handling of the data
   * trash any remaining of the physical sample right after sequencing (we suggest you keep a backup in your lab if we need to resequence)

For sharing the data with you, we need you to indicate on which location we can transfer the data, e.g.:
   * Your project-specific S-drive or S-dataset provided by KU-IT, to which we need access
      *  Read more info about how to create and use a S-drive [here](https://kunet.ku.dk/employee-guide/Pages/IT/S-drive.aspx).
   * You project on [SIF](https://sif.ku.dk) (e.g. ERDA solution for sensitive data), to which we need access
  



Go back to the [Genomics Platform home](https://sundgenomics.github.io)
