## Sequencing Sensitive Data

### Patient sequences are sensitive data
Whether the genomics sequences in themselves without any annotation and related patient data are sensitive or not is a grey zone in the field. However, following hospitals, genomics data repository and a general sense of restriction from the Danish regulations, the Genomics Platform consider the genomics sequences to be sensitive data by themselves and has to treat them as such. 

### Data Processing Agreements and Roles
Processing of sensitive data requires a data processing agreement defining the roles of data controller and data processor(s) as well as how data will be handled between those roles. Genérally speaking, if you come to use with a data containing sensitive data (e.g. sequencing libraries from patient samples), you are the data controller and the Genomics Platform is the (or one of the) data processor.

You can read about KU rules for data processing [here on KUnet](https://kunet.ku.dk/work-areas/research/data/personal-data/dataprocessors/Pages/default.aspx). In short:
   * Personal data must not be processed until a data processing agreement has been signed.
   * Data processing agreements must be registrered in [Workzone - group 515](https://kuforms.ku.dk/xform/frontend/FormEngine/v2/ShowForm.aspx?alias=FA3027&groupId=2&casefolderid=1&doctype=5&formid=4102).
   * University of Copenhagen may perform tasks as data processor for another research institution which is conducting a research project.

### Collaborating outside KU

If [a general data processing agreement exists between KU and the collaboration partner](https://kunet.ku.dk/work-areas/research/data/personal-data/statistics-denmark/Pages/default.aspx), you do not need to make a separate data procesing agreement. Among others, KU has general data processing agreements with [Region Hovestaden](https://www.regionh.dk/english/about-the-capital-region/facts-about-the-region/Pages/Organisational-chart-for-the-Capital-Region-of-Denmark.aspx), which includes several hospitals. Some info here:
>**Data Processing agreement with the Capital Region of Denmark (region H)**  
>The agreement lays down rules for the processing of personal data when the Capital Region of Denmark performs data processing assignments for the University of Copenhagen in connection with research projects. The agreement also lays down rules for the processing of personal data when the University of Denmark performs data processing assignments for the Capital Region of Denmark in connection with research projects.
The agreement covers both data and biological material. 

>**When UCPH processes personal data for the Capital Region**  
>When the University of Copenhagen processes personal data for the Capital Region of Copenhagen, the University of Copenhagen will receive instructions from the Capital Region of Denmark. The instructions must be uploaded in a [UCPH formular](https://kuforms.ku.dk/xform/frontend/FormEngine/v2/ShowForm.aspx?alias=FA3027&groupId=2&casefolderid=1&doctype=5&formid=4102), so that they can be archived in the University of Copenhagen's archiving system. 
    
### What do we need from you

**For data controllers at KU**
   * Link to the data processing agreement registration in  [Workzone - group 515](https://kuforms.ku.dk/xform/frontend/FormEngine/v2/ShowForm.aspx?alias=FA3027&groupId=2&casefolderid=1&doctype=5&formid=4102)

**For data controllers at Capital Region od Denmark (Region H)**

If your collaboration is covered by the general data processing agreement, the genomics Platform will fill [UCPH formular](https://kuforms.ku.dk/xform/frontend/FormEngine/v2/ShowForm.aspx?alias=FA3027&groupId=2&casefolderid=1&doctype=5&formid=4102) to register as Data Processor on your project. To be able to fill beyond the part that is related to the Platform (Registrant and Data processor), the Genomics Platform needs to know from you (see printscreens below):
   * Registration of data controller: Organization, Person, Address
   * Specify purpose: Which box(es) to tick + text description
   * Master Agreement journal number in WorkZone (if any)
   * Specify which data are transferred to companies or collaboration partners (if any)
   * The data processor agreement or the data processing instructions from the Capital Region of Copenhagen

### Our practical workflow
For sensitive data projects, we will generate raw sequencing data on the sequencer only and sync the data also only on the sequencer while it's running (for other runs, we sync the data onto a N-drive while sequencing, but this is not allowed for sensitive data). After that, we need you to indicate on which location we can transfer the data, e.g.:
   * Your project-specific S-drive, to which we need access
   * You project on [SIF](https://sif.ku.dk) (e.g. ERDA solution for sensitive data)

![Form1](./images/Workzone-group515-Form1.png)
![Form2](./images/Workzone-group515-Form2.png)

Go back to the [Genomics Platform home](https://sundgenomics.github.io)
