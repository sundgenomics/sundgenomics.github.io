## Library preparation and index pooling

### Library QC
If you have some questions after training or when following your protocol, please contact us. There are some interesting troubleshooting information from Illumina here.
* [Illumina Library Prep Troubleshooting](https://knowledge.illumina.com/library-preparation/general/library-preparation-general-troubleshooting-list/000001911)


### Index pooling
When pooling libraries to sequence them altogether (aka multiplexing), you need to pay attention to a few things:
* The indexes need to be different enough to maximise the demultiplexing step (ideally, each index pair has at least 3 different bp)
* The overall composition of the indexes on each bp should be diverse enough (in terms of A,T,C,G but also in terms of colors, see Illumina guides below) to optimize the sequencing

 Useful links
* [Illumina NextSeq 1000-2000](https://knowledge.illumina.com/instrumentation/nextseq-1000-2000/instrumentation-nextseq-1000-2000-reference_material-list/000003339)  
* [Illumina Pooling](https://support-docs.illumina.com/SHARE/IndexAdaptersPooling/Content/SHARE/IndexAdaptersPooling/SequencingChemistry.htm)


### Preparing the samplesheet
You can find some more information about the follow-up step (i.e. preparing the samplesheet for future demultiplexing) on [this page](/demux/).
 
Go back to the [Genomics Platform home](https://sundgenomics.github.io)
