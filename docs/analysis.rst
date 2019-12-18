.. _analysis:

Analysis pipeline v5.0
======================

--------
Overview
--------

The version 5.0 MGnify analysis pipeline has significant changes and updates. Deviating from one universal pipeline, it now offers specialised workflows with broadened taxonomic and functional analysis for three data types: amplicon, raw metagenomic or metatranscriptomic reads and assemblies.
Each workflow is defined in common workflow language (`CWL <https://figshare.com/articles/Common_Workflow_Language_draft_3/3115156/2>`_) and utilises the `toil-cwl-runner <https://www.nature.com/articles/nbt.3772>`_ framework. (LINK TO CWL PAGE)

This version includes the following additional analysis:

* Combined coding sequence prediction with Prodigal and FragGeneScan.
* KEGG ortholog annotations.
* KEGG pathway annotations.
* Pfam annotations.
* Presence and absence of Genome Properties.
* antiSMASH annotation of bio-synthetic gene clusters with.
* eggNOG mapper functional annotation.
* Interactive contig viewer.
* Taxonomic assignment for ITS1 and ITS2 regions.
* mOTUs2 marker gene taxonomy.
* DIAMOND and UniRef90 Protein taxonomy.


Updates to databases and software include:

* Quality control - Trimmomatic v0.36
* Taxonomy - MAPseq v1.2.3, ITSoneDB v1.138, UNITE v8.0, mOTUs2 v2.5.1, DIAMOND v0.9.25, UniRef90??
* RNA prediction - Infernal v1.1.2, HMMER v3.2.1, Rfam v13.0, Kronatools v2.7.1
* Coding sequence prediction - FragGeneScan v1.20, PRODIGAL v2.6.3
* Protein annotation - InterProScan v75.0, eggNOG v4.5.1, eggNOG-mapper v1.0.3, antiSMASH v.4.2.0
* Pathway annotation - Genome Properties v2.0.1, kofam_db??

(THERE WAS A TABLED IMAGE OF TOOLS HERE - CHECK IF REQUIRED - IF SO, NEEDS UPDATING ON WEBSITE TOO)

------------------
Amplicon
------------------

Version 5.0 performs taxonomic profiling of large, small subunit ribosomal ribonucleic acid (LSU and SSU rRNA) genes and additionally ITS regions. ITS1 and ITS2 reside between the LSU and SSU genes and are targeted for accurate classification of eukaryotic organisms.
ITS Taxonomy is assigned via two reference databases: `ITSoneDB <https://academic.oup.com/nar/article/46/D1/D127/4210943>`_  (v.1.138) containing ITS1 sequences and
`UNITE <https://academic.oup.com/nar/article/47/D1/D259/5146189>`_ (v8.0) containing ITS1 and ITS2 sequences. Both databases have an 8-level taxonomy, encompassing a a wide range of eukaryotic organisms with focus on fungal sequences.

Amplicon Reads are merged SeqPrep and filtered with an updated version of Trimmomatic, to filter sequences <100bp in length and remove reads with a low average quality score. An additional biopython filtering step removes reads with >10% ambiguous bases.
`Infernal <http://europepmc.org/abstract/MED/24008419>`_ (running in hmm-only mode) uses a library of ribosomal RNA hidden Markov models from `Rfam <http://europepmc.org/articles/PMC4383904>`_ 12.2 to accurately identification of both large and small subunit (:term:`LSU and SSU<LSU, SSU>`) ribosomal ribonucleic acid genes. To identify those we use the families found in the following clans: CL00111 (SSU) and CL00112 (LSU).
These regions are masked prior to ITS classification, minimising cross reactivity.

`MAPSeq <https://www.biorxiv.org/content/10.1101/126953v1>`_ version 1.2.3, offers fast and accurate classification of reads, and provides corresponding confidence scores for assignment at each taxonomic level.

.. figure:: images/pipeline_v5.0_amplicon.png
   :scale: 50 %

**Figure 1**. Overview of the main steps in the amplicon workflow.

------------------
Raw Reads
------------------

Metagenomic and metatranscriptomic raw reads undergo the same preparation, quality control and rRNA classification described for the amplicon workflow.
Various other non-coding RNAs (ncRNAs) are also identified with infernal and available as downloadable files. Families found in the following clans are used to do this: CL00001, CL00002, CL00003.
Supplementary taxonomic classification based on marker gene profiling is performed using `mOTUs2 <https://www.nature.com/articles/s41467-019-08844-4>`_ on quality controlled reads.

FragGeneScan identified predicted coding sequences (pCDS) with masked rRNAs.
Coding sequences are assigned protein annotations from five member databases, with an updated version of InterProScan. Gene ontology terms are extracted from the InterProScan results and grouped by similar functional process.
Additionally, HMMER assigns KEGG orthologs to predicted coding sequences.
Pfam annotations are now provided as separate visualisations and downloads.


Protein Signatures - InterProScan
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Protein signatures are obtained by modelling the conservation of amino acids at specific positions within a group of related proteins (i.e., a protein family), or within the domains/sites shared by a group of proteins. InterPro’s different member databases use different computational methods to produce protein signatures, and they each have their own particular focus of interest: structural and/or functional domains, protein families, or protein features, such as active sites or binding sites (see below).

.. figure:: images/interpro.png
   :scale: 50 %
   :align: center

   **InterPro member databases grouped by the methods used to construct their signatures and focus of interest.**

Only a subset of the InterPro member databases are used by MGnify: Gene3D, TIGRFAMs, Pfam, PRINTS and PROSITE patterns. These databases were selected since, together, they provide both high coverage and offer detailed functional analysis, and have underlying algorithms that can cope with the vast amounts of fragmentary sequence data found in metagenomic datasets.

Assigning GO terms to metagenomic sequences
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
While :term:`InterPro` matches to metagenomic sequence sets are informative in their own right, MGnify offers an additional type of annotation in the form of :term:`Gene Ontology (GO) terms<Go Term>`.

The GO is made up of 3 structured controlled vocabularies that describe gene products in terms of their associated biological processes, cellular components and molecular functions in a species-independent manner. By using GO terms, scientists working on different species or using different databases can compare datasets, since they have a precisely defined name and meaning for a particular concept.

.. figure:: images/go_hier.png
   :align: center

   **An example of GO terms organised into a hierarchy.**

Terms in the GO are ordered into hierarchies, with less specific terms towards the top and more specific terms towards the bottom.  (e.g., alpha-tubulin binding is a type of cytoskeletal binding, which is a type of protein binding). Note that a GO term can have more than one parent term. The Gene Ontology also allows for different types of relationships between terms (such as ‘has part of’ or ‘regulates’). The EMG analysis pipeline only uses the straightforward ‘is a’ relationships. More information about the GO can be found on the GO consortium `documentation page <http://geneontology.org/page/introduction-go-resource>`_.

As part of the metagenomic analysis pipeline, GO terms for molecular function, biological process and cellular component are assigned to :term:`pCDS<Predicted coding sequences (pCDS)>` in a sample by via the InterPro2GO mapping service. This works as follows: :term:`InterPro` entries are given GO terms by curators if the terms can be accurately applied to all of the proteins matching that entry. Sequences searched against InterPro are then associated with GO terms by virtue of the entries they match - a protein that matches one InterPro entry with the GO term ‘kinase activity’ and another InterPro entry with the GO term ‘zinc ion binding’ will be annotated with both GO terms.


KEGG Orthology
^^^^^^^^^^^^^^
`The KEGG orthology database <https://academic.oup.com/nar/article/44/D1/D457/2502600>`_ (KO) contains groups of protein sequences mapped to a high level functional annotation.
A HMMSEARCH against the `KOfam <https://www.biorxiv.org/content/10.1101/602110v1>`_ library; a database of profile HMMs generated for the group of protein sequences in each KO, assigns KO.
Version 5.0 includes a visualised and downloadable summary of the top KEGG orthologs identified in the pCDS.

.. figure:: images/pipeline_v5.0_raw.png
   :scale: 50 %

**Figure 2**. Overview of the main steps in the raw reads workflow.

-----------------
Assembly
-----------------

The functional annotation and taxonomy for assemblies is an extension of those performed for raw reads.

Quality control and filtering are performed at a different length threshold of 500 nucleotides per contig.
Coding sequences are predicted with an in house script utilising both Prodigal and FragGeneScan.

Diamond and UniRef90
^^^^^^^^^^^^^^^^^^^^
In addition to rRNA taxonomy, `DIAMOND <https://www.nature.com/articles/nmeth.3176>`_ assigns taxonomy to protein sequences with reference to the `UniRef90 <https://academic.oup.com/bioinformatics/article/31/6/926/214968>`_ database.
UniRef90 is a database of clustered UniProt sequences at a 90% similarity, with a representative taxonomy assigned to each cluster.
Diamond performs efficient high-throughput pairwise and frame-shift blastp sequence alignment against the UniRef90 database, to assign the top taxonomic hit to each predicted protein sequence.

Genome Properties
^^^^^^^^^^^^^^^^^
In addition to the raw read functional analysis, protein annotations are used to profile the presence and absence of `Genome Properties <https://academic.oup.com/nar/article/47/D1/D564/5144958>`_ (GP).
Each full GP annotation represents the presence of all proteins above a curated threshold, required to reconstruct a particular functional pathway.
GP annotations are performed on InterProScan outputs, maximising the scope of annotation to the 5 member databases. (which is visualised as a hierarchy grouped by higher function?)

KEGG Modules and Pathways
^^^^^^^^^^^^^^^^^^^^^^^^^
KEGG orthologs are augmented by KEGG pathway annotations. Pathways presence and their completeness are illustrated in bar graphs and tables.
KEGG pathways are named by KEGG module, and asserted using network graphs connecting each module with the predicted KEGG orthologs.
The number of missing and matching KEGG orthologs expected in each pathway are calculated, giving a percentage of pathway completeness.

antiSMASH
^^^^^^^^^
antiSMASH is a pipeline designed to identify and annotate biosynthetic gene clusters which code for the production of secondary metabolites.
The antiSMASH tool annotated from a database of biosynthetic signature gene models. It is constructed from HMMER profiles of protein domains known to be present in biosynthetic gene clusters.
The database is used to predict gene cluster boundaries, infer chemical structure and functional annotation. (smCOGS???) The top antiSMASH gene cluster hits are visualised in a bar graph.

eggNOG-mapper and Contig Viewer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
`eggNOG <https://academic.oup.com/nar/article/44/D1/D286/2503059>`_ is an extensive database of orthologous groups (OGs) with functional annotation for eukaryotes and prokaryotes, computed from publicly available genomes and proteomes.
The `eggNOG-mapper <https://www.biorxiv.org/content/10.1101/076331v1.full>`_ tool uses the predefined eggNOG database to assign functional annotations to large protein sequence data-sets.
Clusters of orthologous groups (COGs) and a free-text functional description are visualised on the new contig viewer.
KEGG orthologs, gene ontology terms, PFAM and InterPro annotations are also available on the interactive contig viewer.
The tool allows a user to browse the functional annotations per contig, filtering by a specific cluster or annotation type. The groups within in each annotation type can be colour coordinated to aid visual analysis.


.. figure:: images/pipeline_v5.0_assembly.png
   :scale: 50 %

**Figure 3**. Overview of the main steps in the assembly workflow.