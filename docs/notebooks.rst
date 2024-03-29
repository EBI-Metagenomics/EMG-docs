MGnify Notebooks Server
=======================

A Jupyter Lab environment for the MGnify API
--------------------------------------------

--------------------
Short video tutorial
--------------------

.. raw :: html
    
    <iframe width="560" height="315" src="https://www.youtube.com/embed/B8rw7GTX9GQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

`View on YouTube <https://youtu.be/B8rw7GTX9GQ>`_.

---------------------------------------
About the notebooks.mgnify.org resource
---------------------------------------

The `MGnify Notebooks Server <https://shiny-portal.embl.de/shinyapps/app/06_mgnify-notebook-lab?jlpath=mgnify-examples/home.ipynb>`_
is a `Jupyter Lab <https://jupyter.org>`_ environment for doing data analysis online.

You don’t need to install anything – it is hosted by `EMBL’s Cell Biology & Biophysics Unit <https://www.embl.org/research/units/cell-biology-biophysics/cbbcs/>`_ and you use it in your web browser.

.. figure:: images/notebooks/notebooks-home.png

    The default `"Home" notebook of the MGnify Notebooks Server <https://shiny-portal.embl.de/shinyapps/app/06_mgnify-notebook-lab?jlpath=mgnify-examples/home.ipynb>`_.


.. hint::

    The `Notebooks Server homepage <https://shiny-portal.embl.de/shinyapps/app/06_mgnify-notebook-lab?jlpath=mgnify-examples/home.ipynb>`_ contains a quick starts guide and list of the available Notebooks.


----------------------------------
Use cases for the Notebooks Server
----------------------------------

Programmatic access to MGnify data resources is done via the :doc:`the API <api>`.

The Notebooks are useful if you’re just **starting to explore the API** and are looking for code examples to get started.

They are also useful if you only need to access a few pieces of data and so **don’t want to install anything** to get what you need.

There are examples in `Python <https://shiny-portal.embl.de/shinyapps/app/06_mgnify-notebook-lab?jlpath=mgnify-examples/Python%20Examples>`_ and in the `R language <https://shiny-portal.embl.de/shinyapps/app/06_mgnify-notebook-lab?jlpath=mgnify-examples/R%20Examples>`_.


------------------------------------------
MGnifyR: an R package for accessing MGnify
------------------------------------------

The Notebooks include code examples written using `MGnifyR <https://github.com/beadyallen/MGnifyR/>`_, 
an R package with convenience wrappers around the MGnify API, as well as recipes for cross-study analysis.

MGnifyR is already installed on the Notebook Server, so you can try it out straight away.

Take a look at `this cross-study analysis example <https://shiny-portal.embl.de/shinyapps/app/06_mgnify-notebook-lab?jlpath=mgnify-examples/R%20Examples/Cross-study%20analysis.ipynb>`_.


------------------------
Using a Jupyter Notebook
------------------------

A Jupyter Notebook is an interactive coding document.
It is based on cells (as in blocks of content).
Some cells are just text, and some contain code.

In our examples, there are text cells to explain what we’re doing, and code cells with example code that you can run.

.. hint::
    To run a code cell, select it (with your keyboard/mouse/input device) and press :code:`shift + enter` or click the ▶ icon in the top menubar.

Any output from the code will be printed directly below the code cell.

Only one cells runs at a time, so you can step through a notebook to step through a workflow.

**Each example notebook we provide should run without any changes needed.** You are free to change these as you wish – you’re working on a copy of the examples.

.. warning::
    When you leave your computer for a while or close the website, your instance of the Jupyter Lab will end. Your work **might** be saved if you come back later and refresh, but usually it won’t be: so make sure you download anything you need to keep before finishing.


---------------------------------------------
Jumping to a Notebook from the MGnify website
---------------------------------------------

.. figure:: images/notebooks/website-programmatic-access-box.png

    There are deep-links to some Notebooks from the :doc:`the MGnify website <portal>`.

Some resource views on the MGnify website show a "Programmatic access" banner.
This lists the :doc:`API <api>` URL for the resource, as well as links to any Notebooks that help you consume that API endpoint.

For example, opening a :term:`Study` in R or Python means opening a Notebook on our server with example code to read in that study.

These are `deep links <https://en.wikipedia.org/wiki/Deep_linking>`_, in that following them means the Notebook will already know the Study Accession (ID) you are interested in.


------------------------------------------------
Using the notebooks on your own computer instead
------------------------------------------------

The `code for our notebooks <https://github.com/ebi-Metagenomics/notebooks/>`_ is open source and available on GitHub.

The notebook server is `containerised with Docker <https://www.docker.com/resources/what-container>`_, making `installation <https://github.com/EBI-Metagenomics/notebooks#running-shinyproxy>`_ fairly simple.

You can also simply copy `the notebooks themselves <https://github.com/EBI-Metagenomics/notebooks/tree/main/notebooks-src/notebooks>`_ from GitHub, but you will have to `install the dependencies <https://github.com/EBI-Metagenomics/notebooks/tree/main/dependencies>`_ using e.g. `Conda <https://docs.conda.io/en/latest/miniconda.html>`_.







