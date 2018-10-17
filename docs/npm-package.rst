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

    <script async src="https://jsfiddle.net/mgnify_ebi/w1bp68zj/embed/"></script>


Getting started
^^^^^^^^^^^^^^^

--------------
Data retrieval
--------------

Studies
-------
Retrieving a study by accession

.. raw:: html

    <script async src="https://jsfiddle.net/mgnify_ebi/w1bp68zj/2/embed/"></script>


Retrieving a list of all studies

.. raw:: html

    <script async src="https://jsfiddle.net/mgnify_ebi/anbtye4m/1/embed/"></script>


Retrieving a list of studies related to a sample

.. raw:: html

    <script async src="https://jsfiddle.net/mgnify_ebi/w60Lptzj/2/embed/"></script>


Retrieve a list of sample geo-coordinates for a study

.. raw:: html

    <script async src="https://jsfiddle.net/mgnify_ebi/tzpyumL4/1/embed/"></script>


Retrieve a list of analyses for a study

.. raw:: html

    <script async src="https://jsfiddle.net/mgnify_ebi/45emb18s/3/embed/"></script>


Retrieve all available downloads for a study

.. raw:: html

    <script async src="https://jsfiddle.net/mgnify_ebi/smrun6hp/3/embed/"></script>


Samples
-------
Retrieving a sample by accession

.. raw:: html

    <script async src="https://jsfiddle.net/mgnify_ebi/zc2h6gqs/1/embed/"></script>


Retrieving a list of all samples

.. raw:: html

    <script async src="https://jsfiddle.net/mgnify_ebi/ecug7bvt/1/embed/"></script>

Runs
----

Retrieve a run by accession

.. raw:: html

    <script async src="https://jsfiddle.net/mgnify_ebi/obn35La9/embed/"></script>


Retrieve a list of all runs

.. raw:: html

    <script async src="https://jsfiddle.net/mgnify_ebi/bsrfd5oL/embed/"></script>

Retrieve a list of analyses for a run by accession

.. raw:: html

    <script async src="https://jsfiddle.net/mgnify_ebi/kanr2b0d/1/embed/"></script>

Retrieve a list of analyses of assemblies for a run by run accession

.. raw:: html

    <script async src="https://jsfiddle.net/mgnify_ebi/y6t1wphg/2/embed/"></script>



Analysis
--------
Retrieve an analysis by accession

.. raw:: html

    <script async src="https://jsfiddle.net/mgnify_ebi/zgt0da8n/3/embed/"></script>


Retrieve a list of all downloads for an analysis

.. raw:: html

    <script async src="https://jsfiddle.net/mgnify_ebi/hnp75dg0/embed/"></script>


Biomes
------


Retrieve a biome by lineage

.. raw:: html

    <script async src="https://jsfiddle.net/mgnify_ebi/k9at0r1h/2/embed/"></script>


Retrieve a list of all biomes

.. raw:: html

    <script async src="https://jsfiddle.net/mgnify_ebi/5r0pmacf/embed/"></script>



Retrieve a list of biomes rooted at specified lineage

.. raw:: html

    <script async src="https://jsfiddle.net/mgnify_ebi/2Lw5m7e3/1/embed/"></script>


Publications
------------

Retrieve a publication by id

.. raw:: html

    <script async src="https://jsfiddle.net/mgnify_ebi/4omxs0d5/embed/"></script>


Retrieve a list of all publications

.. raw:: html

    <script async src="https://jsfiddle.net/mgnify_ebi/mw2v8d7z/1/embed/"></script>


Retrieve a list of studies related to a publication

.. raw:: html

    <script async src="https://jsfiddle.net/mgnify_ebi/zer8cjL6/1/embed/"></script>

--------------
Data display
--------------

The following section list examples of how to load data analysis charts seen on the MGnify website.

QC chart
--------

.. raw:: html

    <script async src="https://jsfiddle.net/mgnify_ebi/3q5ov9u1/embed/"></script>

Taxonomy charts
---------------
The taxonomy pie, column and stacked column charts can all be loaded using the same parameters;
the following example is therefore compatible with any of the 3 classes by changing the instantiated class name (TaxonomyPie, TaxonomyColumn & TaxonomyColumnStacked)

.. raw:: html

    <script async src="https://jsfiddle.net/mgnify_ebi/02wamts1/1/embed/"></script>

Nucleotide position histogram
-----------------------------

.. raw:: html

    <script async src="https://jsfiddle.net/mgnify_ebi/4stdgrpm/embed/"></script>


Interpro match pie chart
------------------------

.. raw:: html

    <script async src="https://jsfiddle.net/mgnify_ebi/Lktuqd67/embed/"></script>


Reads length histogram and sequence length bar chart
----------------------------------------------------

.. raw:: html

    <script async src="https://jsfiddle.net/mgnify_ebi/2boc7Lrj/embed/"></script>


Reads GC Distribution & GC/AT content
-------------------------------------

.. raw:: html

    <script async src="https://jsfiddle.net/mgnify_ebi/xgw1e43a/embed/"></script>


Go Term charts
--------------
The following chart can also be loaded in bar chart form using the GoTermBarChart class.

.. raw:: html

    <script async src="https://jsfiddle.net/mgnify_ebi/xa0o29dh/embed/"></script>


Sequence feature summary
------------------------

.. raw:: html

    <script async src="https://jsfiddle.net/mgnify_ebi/6m25oqn9/2/embed/"></script>

