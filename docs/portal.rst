Website and portal
==================
---------------------------------------
'Associated runs' table on project page [not sure if we need this but it was in the Google spreadsheet]
---------------------------------------
This table lists all samples and runs associated with a project as well as the experiment type (Amplicon, Assembly, Metagenomic, Metabarcoding or Metatranscriptomic), sequencing instrument model and pipeline version for each individual run.  

In addition, the last field displays links to analysis results and download pages ( the latter being represented by the icon '.. image:: images/download_i.jpg').

The 'Analysis results' field could also displays two types of messages:

- 'QC not passed’: this message indicates that no sequences survived the filtering occurring during the QC steps. This could be due to base quality filtering, ambiguous base filtering or length filtering.
- ‘Unable to process’: this message indicates that no data suitable for analysis were available for this run. The sequences may not be available in ENA, failed to merge, in the case of pair-end reads, or be in an insuitable format.

---------------
Comparison tool
---------------
Comparing runs helps to identify feature associated with experimental factors. EBI Metagenomics has developed a Comparison Tool that allows user to compare the GO-slim terms associated with the runs of a project (see `Analysis pipeline`_).

**To use the current tool select the corresponding tab from any EMG webpage:**

- The first step is to select the project of interest. They are listed by title in alphabetical order. You can search the project list by entering the first letters of the title from the project you’re interested in.
- Clicking on the ‘More info about selected project’ link, located below the Project list, after selecting a project, will open a new browser window displaying the project page.
- Upon project selection, the 'Run list' window will be populated with the list of runs associated with the project and suitable for comparison. You can select all runs (using the ‘Select all’ link below the window) or up to 30 runs (by using the Ctrl key for Windows PC or Command key on Mac).
- Users can select the ‘Advanced settings’ link to have the options to set the relative abundance threshold for the GO terms to appear in the stack columns, the format of heatmap generated and the number of GO terms with most variation to display in the representations. To start the comparison for your selection, simply click on ‘Compare’.  

**The page will now displays the selected runs and project above 5 new tabs:** 

- The first one is a barcharts representation with 3 dynamic graphs, corresponding to the 3 GO terms categories (see `Analysis pipeline`_). On each, the GO terms and their relative abundance in each selected run is displayed. Hovering the mouse pointer above a bar will display the relative abundance values for this term in the corresponding run. You can export these barcharts representation in PNF, PDF or SVG format using the tool on the top right hand side.   
- The second tab contains stacked column representations with the same dynamic properties than in the barcharts with the addition of the possibility to hide one or more terms of choice by selecting them from the list displayed below each category graph.  
- The third tab presents heatmaps allowing to quickly identified patterns between the selected runs based on the relative abundance of the GO terms. There is currently no export function for this page although the images, being static, can be directly copied.  
- The fourth tab contains dynamic Principal Component Analysis graphs which represent the amount of variance, based on the relative abundance of the GO terms, between the runs for each GO category. Selecting a rectangular region with the mouse pointer will zoom in, which help to separate clustered run markers. The export function allows to download all or the enlarged region.  
- The last tab is a searchable table where you can see the absolute and relative abundance of a given GO term for each run. It is based on the ‘Analysis_summary’ abundance table available from the project page. You can search the table using the run identifier, GO name, GO category, GO id or even absolute or relative abundance.  

We are working with collaborators to develop this tool in order to be able to compare taxonomic annotations, provide statistical validations and compare runs between projects.

-----------
search tool
-----------
