.. _npmpackage:

JS npm package
==============

The MGnify npm JS package is an AMD module which can be built into to retrieve and display data directly from the MGnify api.


Current npm package version is **0.5.2**

Installation
^^^^^^^^^^^^
-----------
Server-side
-----------
.. highlight:: bash

::

    npm install mgnify --save



Example usage
.. highlight:: javascript

::
    // To load data-fetch api only

    const api = require('mgnify').api;
    const study = new api.Study({accession: 'MGYS00000410'});

    // To use charts:

    const charts = require('mgnify').charts;

    // using existing api instance
    const qcChart = new charts.QcChart('containerID', {apiConfig: api});

    // alternately:
    const apiConfig = {API_URL: 'http://localhost:9000/metagenomics/api/v1/'};
    const qcChart = new charts.QcChart('containerID', {apiConfig: apiConfig});


-----------
Client side
-----------
.. raw:: html

    <script async src="http://jsfiddle.net/eqvkoc25/3/embed/"></script>

Getting started
^^^^^^^^^^^^^^^


--------------
Data retrieval
--------------

Studies
-------
Retrieving a study by accession

.. raw:: html

    <script async src="http://jsfiddle.net/mboland/8qan4uL2/5/embed/"></script>


Retrieving a list of all studies

.. raw:: html

    <script async src="http://jsfiddle.net/mboland/8jg73bdc/embed/"></script>


Retrieving a list of studies related to a sample

.. raw:: html

    <script async src="http://jsfiddle.net/mboland/7ag10x9h/3/embed/"></script>


Retrieve a list of sample geo-coordinates for a study

.. raw:: html

    <script async src="http://jsfiddle.net/mboland/d6va9pjz/embed/"></script>


Retrieve a list of analyses for a study

.. raw:: html

    <script async src="//jsfiddle.net/mboland/8fvspjr0/embed/"></script>


Samples
-------
Retrieving a sample by accession

.. raw:: html

    <script async src="http://jsfiddle.net/mboland/ahkgsdet/embed/"></script>


Retrieving a list of all samples

.. raw:: html

    <script async src="http://jsfiddle.net/mboland/m3kbtg0x/embed/"></script>

Runs
----

Retrieve a run by accession

.. raw:: html

    <script async src="http://jsfiddle.net/mboland/dfwz04s3/embed/"></script>


Retrieve a list of all runs

.. raw:: html

    <script async src="http://jsfiddle.net/mboland/peghuxs2/embed/"></script>

Retrieve a list of analyses for a run by accession

.. raw:: html

    <script async src="//jsfiddle.net/mboland/dfwz04s3/2/embed/"></script>

Retrieve a list of analyses of assemblies for a run by run accession

.. raw:: html

    <script async src="//jsfiddle.net/mboland/56zbvcou/embed/"></script>



Analysis
--------
Retrieve an analysis by accession

.. raw:: html

    <script async src="//jsfiddle.net/mboland/sotmdjr9/embed/"></script>


Retrieve an analysis by accession

.. raw:: html

    <script async src="//jsfiddle.net/mboland/sotmdjr9/embed/"></script>



Biomes
------


Retrieve a biome by lineage

.. raw:: html

    <script async src="http://jsfiddle.net/mboland/1jr9g0xk/2/embed/"></script>


Retrieve a list of all biomes

.. raw:: html

    <script async src="http://jsfiddle.net/mboland/vt09une4/2/embed/"></script>



Retrieve a list of biomes rooted at specified lineage

.. raw:: html

    <script async src="http://jsfiddle.net/mboland/w9o6u2xs/embed/"></script>



StudyDownloads
AnalysisDownloads
QCChartData
QCChartStats
Publication
PublicationCollection
PublicationStudies

--------------
Data display
--------------

The following section list examples of how to load data analysis charts seen on the MGnify website.

QC chart
--------

.. raw:: html

    <script async src="http://jsfiddle.net/mboland/3rfpoh6y/22/embed/"></script>

Taxonomy charts
---------------
The taxonomy pie, column and stacked column charts can all be loaded using the same parameters;
the following example is therefore compatible with any of the 3 classes by changing the instantiated class name (TaxonomyPie, TaxonomyColumn & TaxonomyColumnStacked)

.. raw:: html

    <script async src="http://jsfiddle.net/mboland/auk2fxpz/embed/"></script>

Nucleotide position histogram
-----------------------------

.. raw:: html

    <script async src="http://jsfiddle.net/mboland/9a48jtq3/embed/"></script>


Interpro match pie chart
------------------------

.. raw:: html

    <script async src="http://jsfiddle.net/mboland/c6efpjyu/embed/"></script>


Reads length histogram and sequence length bar chart
----------------------------------------------------

.. raw:: html

    <script async src="http://jsfiddle.net/mboland/0doqmvj2/embed/"></script>


Reads GC Distribution & GC/AT content
-------------------------------------

.. raw:: html

    <script async src="http://jsfiddle.net/mboland/vLqa6ehb/embed/"></script>


Go Term charts
--------------
The following chart can also be loaded in bar chart form using the GoTermBarChart class.

.. raw:: html

    <script async src="http://jsfiddle.net/mboland/c6efpjyu/1/embed/"></script>


Sequence feature summary
------------------------

.. raw:: html

    <script async src="http://jsfiddle.net/mboland/tby0fL2o/4/embed/"></script>

