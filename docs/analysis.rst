.. _analysis:

Analysis pipeline
=================

------------------
Taxonomic analysis
------------------
EBI Metagenomics provides taxonomic analysis of sequences predicted to be 16S rRNAs using `Qiime <http://qiime.org/>`_ and the `GreenGenes <http://greengenes.lbl.gov/cgi-bin/nph-index.cgi>`_ database for annotation.

The presence of 16S rRNA sequences in reads are predicted using `HMMER <http://www.hmmer.org>`_ and prokaryotic rRNA models from `Rfam <http://rfam.xfam.org>`_ in forward and reverse orientation. The predicted 16S rRNA sequences are extracted from the reads and annotated using the Qiime `closed-reference protocol <http://qiime.org/tutorials/otu_picking.html>`_ for version 2 and higher of the pipeline. The taxonomic lineages are provided in at the kingdom, phylum, class, order, family, genus and species taxonomic levels (labelled k, p, c, o, f, g and s, respectively). Predicted 16S rRNA sequences that were not annotated by Qiime are grouped at the ‘Root’ level.

-------------------
Functional analysis
-------------------
Functional analysis of predicted coding sequences (pCDS) from metagenomic data is provided using the `InterProScan <https://www.ebi.ac.uk/interpro/interproscan.html>`_ software provided by the `InterPro <https://www.ebi.ac.uk/interpro/>`_ database. InterPro is a sequence analysis resource that predicts protein family membership, along with the presence of important domains and sites. It does this by combining predictive models known as protein signatures from a number of different databases into a single searchable resource. InterPro curators manually integrate the different signatures, provide names and descriptive abstracts and, whenever possible, add Gene Ontology (GO) terms.

Protein signatures
^^^^^^^^^^^^^^^^^^
Protein signatures are obtained by modelling the conservation of amino acids at specific positions within a group of related proteins (i.e., a protein family), or within the domains/sites shared by a group of proteins. InterPro’s different member databases use different computational methods to produce protein signatures, and they each have their own particular focus of interest: structural and/or functional domains, protein families, or protein features, such as active sites or binding sites (see below).

.. figure:: images/interpro.png
   :scale: 50 %
   :align: center

   **InterPro member databases grouped by the methods used to construct their signatures and focus of interest.**

Only a subset of the InterPro member databases are used by EBI Metagenomics: Gene3D, TIGRFAMs, Pfam, PRINTS and PROSITE patterns. These databases were selected since, together, they provide both high coverage and offer detailed functional analysis, and have underlying algorithms that can cope with the vast amounts of fragmentary sequence data found in metagenomic datasets. 


Assigning GO terms to metagenomic sequences
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
While InterPro matches to metagenomic sequence sets are informative in their own right, EBI Metagenomics offers an additional type of annotation in the form of Gene Ontology (GO) terms.

The GO is made up of 3 structured controlled vocabularies that describe gene products in terms of their associated biological processes, cellular components and molecular functions in a species-independent manner. By using GO terms, scientists working on different species or using different databases can compare datasets, since they have a precisely defined name and meaning for a particular concept.

.. figure:: images/go_hier.png
   :align: center

   **An example of GO terms organised into a hierarchy.**

Terms in the GO are ordered into hierarchies, with less specific terms towards the top and more specific terms towards the bottom.  (e.g., alpha-tubulin binding is a type of cytoskeletal binding, which is a type of protein binding). Note that a GO term can have more than one parent term. The Gene Ontology also allows for different types of relationships between terms (such as ‘has part of’ or ‘regulates’). The EMG analysis pipeline only uses the straightforward ‘is a’ relationships. More information about the GO can be found on the GO consortium `documentation page <http://www.geneontology.org/GO.doc.shtml>`_.

As part of the metagenomic analysis pipeline, GO terms for molecular function, biological process and cellular component are assigned to pCDS in a sample by via the InterPro2GO mapping service. This works as follows: InterPro entries are given GO terms by curators if the terms can be accurately applied to all of the proteins matching that entry. Sequences searched against InterPro are then associated with GO terms by virtue of the entries they match - a protein that matches one InterPro entry with the GO term ‘kinase activity’ and another InterPro entry with the GO term ‘zinc ion binding’ will be annotated with both GO terms.

------------
Output files
------------
EBI Metagenomics analysis pipeline produces a number of files underlying the charts displayed on the website. These files are available via the 'Download' tab accessible on the run page.
The Download tab is organised in 3 sections: ‘Sequence data’, ‘Functional analysis’ (not available in the case of amplicon runs)  and ‘Taxonomic analysis’.
The first and second sections contain a number of sequence files in FASTA format. To facilitate the download process, these files are compressed with `GZIP <http://www.gzip.org/>`_ and when too large to be easily transferable, chunked in manageable size. If it is the case, please download all chunks, decompress them and concatenate them to reconstitute the full file.

Description of fasta files available to download
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- Processed nucleotide reads: this file contains all reads having passed the quality control (QC) step.
- Processed reads with pCDS: this file contains all processed reads having having predicted CDS(s) (pCDS). The CDS prediction is performed using `FragGenScan <http://omics.informatics.indiana.edu/FragGeneScan>`_ on the reads having passed the QC after masking of predicted rRNA and tRNA.
- Processed reads with annotation: this file contains all processed reads containing pCDS(s) annotated by `InterProScan <https://www.ebi.ac.uk/interpro/interproscan.html>`_.
- Processed reads without annotation: this file contains all processed reads having pCDS(s) not annotated by InterProScan
- Predicted CDS with annotation : this file contains all the predicted proteins having been annotated by InterProScan. The sequence headers are: <run_id>_<start of pCDS>_<end of pCDS>_<strand of pCDS><space><InterPro term>/<member database ID>/<start of hit in predicted protein>-<end of hit in predicted protein>.
- Predicted CDS without annotation: this file contains all the predicted proteins not annotated by InterProScan. The sequence headers are <run_id>_<start of pCDS>_<end of pCDS>_<strand of pCDS>.
- Predicted ORF without annotation: this file contains all the pCDS coding for predicted proteins that were not annotated by InterProScan. The sequence headers are <run_id>_<start of pCDS>_<end of pCDS>_<strand of pCDS>.
- Predicted tRNAs: this file contains all the sequences predicted to encode tRNAs. The prediction was done using models from `Rfam <http://rfam.xfam.org>`_ with `Hmmer tools <http://hmmer.org>`_.
- Reads encoding 5S rRNA: this file contains all reads predicted to encode for 5S rRNA by rRNASelector.
- Reads encoding 16S rRNA: this file contains all reads predicted to encode for 16S rRNA by rRNASelector.
- Reads encoding 23S rRNA: this file contains all reads predicted to encode for 23S rRNA by rRNASelector.

Description of functional annotation files available to download
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- InterPro matches file:  it is a tab-delimited file containing 15 columns. They are fully described `here <https://github.com/ebi-pf-team/interproscan/wiki/OutputFormats>`_
- Complete GO annotation file: it is a comma-separated file containing 4 colums. The first column lists the GO terms (labelled GO:XXXXXXX) having been associated with the predicted CDSs. The second gives the GO term description while the third indicates which category the GO term belong to. There is 3 category: ‘biological process’ (higher biological process such as ‘rRNA modification’) , ‘molecular function’ (individual catalytic activity such as ‘mannosyltransferase activity’) and ‘cellular component’ (cellular localisation of the activty such as ‘mitochondrion’). The last column give the number of predicted CDSs having been annotated with the GO terms for the run.
- GO slim annotation file: this file is derived from the 'Complete GO annotation file' and has the same format. The GO slim set is a cut-down version of the GO terms containing a subset of the terms in the whole GO. They give a broad overview of the ontology content without the details of the specific fine grained terms. Go slim terms are used for visualisation on the website. To illustrate how the GO slim terms relates to the GO terms, the different metal binding GO terms present in the ‘Complete GO annotation’ file are summarized as one generic metal binding term in the ‘GO slim annotation’ file. The last column give the number of predicted CDSs having been annotated with the GO slim terms for the run.

Description of taxonomic assignment files available to download
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- OTUs, reads and taxonomic assignments files: these  files contain the same data presented in 3 differnt format : tab-separated file (TSV) and two Biom file (HD5F and JSON). The TSV file contains 3 columns which headers are in the second line of the file. The first column is the OTU Id. The second column indicates the number of predicted 16S sequences associated with each OTU. The third column contains the taxonomic lineages provided by `GreenGenes database <http://greengenes.lbl.gov/cgi-bin/nph-index.cgi>`_. Note that the number of unannotated 16S sequences is not indicated in this file. This file can be directly imported into `Megan6 <http://ab.inf.uni-tuebingen.de/software/megan6/>`_ for visualisation and further analysis. The OTU id can be compared between runs for version 2 and 3 of the pipeline as they have been generated using `Qiime closed-reference protocol <http://qiime.org/tutorials/otu_picking.html>`_.The Biom files are `computer-readable files <http://biom-format.org>`_. The HD5F (Hierachical Data Format) format can be imported into analysis and visualisation tools such as Matlab and R. A larger number of commercial and freely available tools, such as MEGAN6, can consume the JavaScript Object Notation (JSON) format.
- Phylogenetic tree (Newick format)’ file (only available up to version 3 of EBI Metagenomics pipeline): this file can be used to visualise the hierarchical distribution of the taxonomic lineages of each run. The `Newick format <https://en.wikipedia.org/wiki/Newick_format>`_ is a computer-readable format to represent the tree and can be directly imported into freely-available viewers such as `FigTree <http://tree.bio.ed.ac.uk/software/figtree>`_ and `ITOL (interactive Tree of Life) <http://itol.embl.de>`_.

-------------
Summary files
-------------
In addition to the output files for individual runs, EBI Metagenomics provides a number of summary files available via the 'Analysis summary' tab on the project page. They summarized the counts per feature across all runs of a study and therefore provide an easy way to identify patterns. The summary files are split between functional (not available for amplicon-only study) and taxonomy sections.

functional summary files
^^^^^^^^^^^^^^^^^^^^^^^^
- InterPro matches(TSV): this tab-separated file contains 2 designation columns followed by a column for each valid runs of the project. The first column lists the InterPro terms having been associated to the predicted CDSs. The second column gives the description of the InterPro terms. All columns labelled with a run identifier present the number of predicted CDSs having been annotated with each InterPro terms for this run.
- Complete GO annotation (TSV): this file contains 3 designation columns followed by a column for each valid runs of the project. The first column lists the GO terms (labelled GO:XXXXXXX) having been associated to the predicted CDSs. The second column gives the GO term description while the third column indicates which category the GO term belong to. All columns labelled with a run identifier present the number of predicted CDSs having been annotated with each GO terms for this run.
- The ‘GO slim annotation (TSV)’ file is derived from the ‘Complete GO annotation’ file and has the same format. The GO slim term set is a cut-down version of the GO terms containing a subset of the terms in the whole GO. They give a broad overview of the ontology content without the detail of the specific fine grained terms. 

taxonomy summary files
^^^^^^^^^^^^^^^^^^^^^^
- Taxonomic assignments (TSV): this file contains one ‘Taxonomy’ column followed by a column for each valid runs of the project. The ‘Taxonomy’ column list the taxonomic lineages having been associated with the predicted 16S sequences. All columns labelled with a run identifier present the number of predicted 16S sequences having been annotated with the taxonomic lineages for this run. This file can be directly imported into `Megan6 <http://ab.inf.uni-tuebingen.de/software/megan6/>`_ for visualisation and further analysis.
- The ‘Phylum level taxonomies (TSV)’ file is derived from the ‘Taxonomic assignments’ file and presents the assignments brought up to ‘phylum’ level in order to give a high level view of the taxonomic assignments. The two first columns of this file present the ‘kingdom’ and ‘phylum’ level assignments, respectively. All columns labelled with a run identifier present the number of predicted 16S sequences having been annotated with the ‘phylum’ level taxonomic lineages for this run.


