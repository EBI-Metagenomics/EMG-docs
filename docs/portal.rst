Website and portal
==================
------------------------------------------------------
Content of the 'Associated runs' table on project page 
------------------------------------------------------

This table lists all samples and runs associated with a project as well as the experiment type (Amplicon, Assembly, Metagenomic, Metabarcoding or Metatranscriptomic), sequencing instrument model and pipeline version for each individual run.  
In addition, the last field displays links to analysis results and download pages (the latter being represented by the icon |test|). 

.. |test| image:: images/download_IC.png

The 'Analysis results' field could also displays two types of messages:

- 'QC not passed’: this message indicates that no sequences survived the filtering occurring during the QC steps. This could be due to base quality filtering, ambiguous base filtering or length filtering.
- ‘Unable to process’: this message indicates that no data suitable for analysis were available for this run. The sequences may not be available in ENA, failed to merge, in the case of pair-end reads, or be in an insuitable format.

------------------------------------------------------------
Finding functional information about runs on the EMG website
------------------------------------------------------------

Functional analysis of runs within projects on the `_EMG website <www.ebi.ac.uk/metagenomics/>`__ can be accessed by clicking on the Functional Analysis tab found toward the top of any run page (see Figure Z below). Note that this tab will be greyed for amplicon runs.

[]
Figure Z. A Functional analysis tab can be found towards the top of each run page.

Clicking on this tab brings up a page displaying sequence features ('number of reads with predicted CDS (pCDS)', 'number of reads with predicted RNA', 'number of reads with InterPro matches', 'number of pCDS' and 'number of pCDS with InterPro match'), InterPro match information and GO term annotation for the run, as shown in Figure XX below.

[]
Figure XX. Functional analysis of metagenomics data, as shown on the EMG website. A) InterPro match information for the predicted coding sequences in the run is shown. The number of InterPro matches are displayed graphically, and as a table that has a text search facility.  B) The GO terms predicted for the sample are displayed. Different graphical representations are available, and can be selected by clicking on the ‘Switch view’ icons.

The Gene Ontology terms displayed graphically on the web site have been ‘slimmed’ with a special GO slim developed for metagenomic data sets. GO slims are cut-down versions of the Gene Ontology, containing a subset of the terms in the whole GO. They give a broad overview of the ontology content without the detail of the specific fine-grained terms.
 
The full data sets used to generate both the InterPro and GO overview charts, along with a host of additional data and intermediate files (processed reads, pCDS, reads encoding RNA and taxonomic analysis  results) can be downloaded for further analysis by clicking the Download tab, found towards the top of the page (see complete description `here <https://github.com/ProteinsWebTeam/EMG-docs/blob/master/docs/analysis.rst>`__).

---------------
Comparison tool
---------------
Comparing runs helps to identify feature associated with experimental factors. EBI Metagenomics has developed a Comparison Tool that allows user to compare the GO-slim terms associated with the runs of a project (see `Analysis pipeline <https://github.com/ProteinsWebTeam/EMG-docs/blob/master/docs/analysis.rst>`__).

**To use the current tool, select the corresponding tab from any EMG webpage:**

- The first step is to select the project of interest. They are listed by title in alphabetical order. You can search the project list by entering the first letters of the title from the project you’re interested in.
- Clicking on the ‘More info about selected project’ link, located below the Project list, after selecting a project, will open a new browser window displaying the project page.
- Upon project selection, the 'Run list' window will be populated with the list of runs associated with the project and suitable for comparison. You can select all runs (using the ‘Select all’ link below the window) or up to 30 runs (by using the Ctrl key for Windows PC or Command key on Mac).
- Users can select the ‘Advanced settings’ link to have the options to set the relative abundance threshold for the GO terms to appear in the stack columns, the format of heatmap generated and the number of GO terms with most variation to display in the representations.   

**To start the comparison for your selection, simply click on ‘Compare’.** 
The page will now display the study and selected runs on top of 5 new comparison tabs:  

- The first one is a barcharts representation with 3 dynamic graphs, corresponding to the 3 GO terms categories (see `Analysis pipeline <https://github.com/ProteinsWebTeam/EMG-docs/blob/master/docs/analysis.rst>`__). On each, the GO terms and their relative abundance in each selected run is displayed. Hovering the mouse pointer above a bar will display the relative abundance values for this term in the corresponding run. You can export these barcharts representation in PNF, PDF or SVG format using the tool on the top right hand side.   
- The second tab contains stacked column representations with the same dynamic properties than in the barcharts with the addition of the possibility to hide one or more terms of choice by selecting them from the list displayed below each category graph.  
- The third tab presents heatmaps allowing to quickly identified patterns between the selected runs based on the relative abundance of the GO terms. There is currently no export function for this page although the images, being static, can be directly copied.  
- The fourth tab contains dynamic Principal Component Analysis graphs which represent the amount of variance between runs, based on the relative abundance of the GO terms, between the runs for each GO category. Selecting a rectangular region with the mouse pointer will zoom in, which help to separate clustered run markers. The export function allows to download all or the enlarged region.  
- The last tab is a searchable table where you can see the absolute and relative abundance of a given GO term for each run. It is based on the ‘Analysis_summary’ abundance table available from the project page. You can search the table using the run identifier, GO name, GO category, GO id or even absolute or relative abundance.  

We are working with collaborators to develop this tool in order to be able to compare taxonomic annotations, provide statistical validations and compare runs between projects.

-----------------------------------------
Data discovery on EBI Metagenomics portal
-----------------------------------------

EBI metagenomics is the largest metagenomic resource of public datasets. In order to help users accessing the data present on the portal, EBI Metagenomics offers a powerful search tool and a range of browsing options.

Search tool
^^^^^^^^^^^
The Search tool, underlayed by `EBI search <https://www.ebi.ac.uk/ebisearch/overview.ebi>`_, can be accessed from any page using the 'search' tab or the 'search' buttom located on the right of the EBI Metagenomics banner. The search space can be restricted using the 'search' field from the latter.

The search page contains 3 tabs allowing users to navigate between project, sample and run search levels. In each tab, the left hand side panel provide a number of facets that can be used to restrict the search space.

- at the project level, the search can be restricted by 'biome' and 'centre name'. Selection of any of the facets will impact the search at sample and run level in order to be able to drill down into the results. Search results can be donwloaded as tab-separated file.
- at the sample level, in addition to 'biome', the choice of facets includes 'temperature', 'depth', 'sequencing method', 'sample origination', 'disease status' and 'phenotype', when provided. Note that these metadata are provided by the data submitter and are not curated.
- at the run level, users can restrict their searches according to 'biome', 'temperature', 'depth', 'pipeline version', 'organism', 'experiment type' as well as Go and InterPro terms.

Browsing options
^^^^^^^^^^^^^^^^

- Public project can be accessed using the links corresponding to the number of projects, samples and runs or experiment types located on the EBI Metagenomics home page below the main banner. Selecting one of those will redirect users to the corresponding EBI Metagenomics search page.
- Another way to discover data of interest is to browse the public projects by biome as displayed on the EBI Metagenomics homepage. The 10 biomes with higher number of projects are displayed by default however the list can be extended using the 'See all biomes' link.  Upon selection, a table giving the hierarchical lineage according to `GOLD database classification <https://gold.jgi.doe.gov/distribution#Classification>`_  is provided. On the right hand-side of this table, the number of projects associated to the lineage in the strict sense or including sub-lineages are displayed as dynamic links giving access to the selected projects.
- Users can also access particular projects, or samples, using the corresponding tabs located above the EBI Metagenomics banner. The list of projects, or samples, can be restricted using the Biome drop-down menu and/or text search. The results of this filtering can be downloaded using the two spreadsheet icons located above the right hand-side of the tables.
- Finally, users have the option to access, from the EBI Metagenomics homepage, the latest public projects uploaded via the right side of the 'Browse projects' section.
