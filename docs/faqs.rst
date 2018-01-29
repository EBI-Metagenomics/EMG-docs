.. _faq:

FAQs
=====

What kind of sequence data does the service accept?
---------------------------------------------------
EBI Metagenomics accepts sequencing data from a wide range of platforms, including Roche 454, Illumina and Ion Torrent. In addition to analysis of whole-genome shotgun (WGS) sequenced metagenomic and metatranscriptomic samples, it also provides analysis of 16S ribosomal RNA (rRNA) amplicon data. If you would like to submit Oxford Nanopore sequences, we suggest you `contact us <metagenomics-help@ebi.ac.uk>`_ prior to submission.

Can I submit assembled metagenomic sequences for analysis?
----------------------------------------------------------
Yes, we welcome submission of assembled data.

Can I submit 18S rRNA or ITS amplicon sequences?
------------------------------------------------
At the present moment, the pipeline does not provide taxonomic analysis of 18S rRNA or ITS sequences, so no meaningful analysis results will be returned for these data sets.

Can I submit viral sequences?
-----------------------------
Although EBI Metagenomics does not currently provide taxonomic analysis of viral sequences, any reads submitted to the pipeline that encode predicted protein coding sequences (pCDS) undergo functional analysis using InterPro. Therefore, while no taxonomic data will be returned for viral sequences, it should be possible to obtain functional analysis results.

How do I run a BLAST search against the metagenomics datasets?
--------------------------------------------------------------
We don't offer BLAST searches against our metagenomic data sets via the web site. We do not have the resources to offer this service, owing to the size of the data. If you wish to perform such an analysis, You would will need to download the data locally and index it for BLAST. We do provide `scripts <https://github.com/ProteinsWebTeam/ebi-metagenomics/wiki/Downloading-results-programmatically>`_ for bulk download of results files, which may prove useful.

Can I change the release date of my project?
--------------------------------------------
The date of release is set by you during the submission in ENA. If you do not explicitly choose a date, it is set to two years from the submission date by default. You can reduce or extend the release date by going to the 'Submit & update' page of the ENA website, logging in using your Webin account id, selecting the relevant study and then clicking the pen icon near the current release date to alter it.

How long will it take for my data to be analyzed?
-------------------------------------------------
We aim to analyze submitted data as quickly as possible. However, submitted data are only available to us once they have been validated and archived by ENA. This process takes at least 24 hours, and in some cases several days. Once the sequence files are made available, the analysis time depends on our current analysis backlog, the size and number of runs in the project you have submitted. Most studies will be validated, archived and analysed within one week. If you are concerned that your data is taking a long time to be analysed, please `contact us <metagenomics-help@ebi.ac.uk>`_.

I have submitted my data - how do I trigger the analysis?
---------------------------------------------------------
There is no manual way to trigger analysis. If you have provided `access agreement <https://www.ebi.ac.uk/metagenomics/submission>`_ for EBI Metagenomics, we will pick up your sequences from ENA automatically and queue them for analysis. 

Do you have an API?
-------------------
To provide a richer search and retrieval interface, we have begun development of a :ref:`restapi`, providing programmatic access to the data.

How can I download several sets of data?
----------------------------------------
While we currently do not have an API, we have Python scripts allowing users to automatically download most processed files from the EBI Metagenomics website. The scripts and instructions for bulk downloading from the latter resource can be found `here <https://github.com/ProteinsWebTeam/ebi-metagenomics/wiki/Downloading-results-programmatically>`_. 

How can I bulk download meta-data?
-----------------------------------
Most of the meta-data associated with projects is taken from the ENA. While EBI Metagenomics does not currently provide an API, the ENA do provide this service, which can be used as a stop gap until our API is in place (`ENA's API documentation <https://www.ebi.ac.uk/ena/portal/api/>`_)

How can I re-analyse my data with a different version of the pipeline?
----------------------------------------------------------------------
It is possible to analyse data sets with different versions of our analysis pipeline. The original analyses are not deleted and are available side by side on our web site. Users interested in having data re-analysed should `contact <metagenomics-help@ebi.ac.uk>`_ us.

Can I request that a dataset is analyzed if I am not the original submitter?
----------------------------------------------------------------------------
We are currently working through the analysis of all publicly available metagenomic datasets in ENA, so if there is a publicly available study that you would like to see analysed in EBI Metagenomics, please get in touch and we will prioritise it.

Can I request my data to not be analyzed by EBI Metagenomics?
-------------------------------------------------------------
We can only access private data for analysis if you gave us agreement to do so. If, for any reasons, you do not want EBI Metagenomics to analyze one of your datasets, please `contact us <metagenomics-help@ebi.ac.uk>`_ .
If your data are public in ENA, then we can access them for analysis in any case.

Can I compare the taxonomic assignments between runs of a project?
-------------------------------------------------------------------
The current version of the comparison tool let you only compare the GO annotations for runs of the same project. We are currently working on extending the functionality to taxonomy but this is not yet ready for release.
In the meantime, please have a look at the summary files provided on the project page. They summarized the counts per feature across the runs and provide an easy way to identify patterns.

The 'OTUs, reads and taxonomic assignments.tsv' can be directly imported into  `Megan 6 <http://ab.inf.uni-tuebingen.de/software/megan6/>`_ to perform comparison and visualisation. The Biom format can also be imported into third-party tools.

Can I know which bacteria encodes particular pCDS in my dataset?
----------------------------------------------------------------
The short answer is that it is generally not possible. The reason is that we annotate directly the reads and select the reads containing 16S for taxonomy assignments. The protein prediction is then performed on all reads after masking the tRNA and rRNA sequences. To link a predicted protein to a taxonomic assignments, the protein-coding gene would need to be on the same read than the annotated 16S sequence. It is possible to check if this is the case using the sequence headers from the 'Interpro matches.tsv' and 'Reads encoding 16S rRNA.fasta' files, both available on the 'Download' for each run.
The same answer applies to assembly although, depending on the contig length, more protein-coding genes may be located near a 16S rRNA genes.


