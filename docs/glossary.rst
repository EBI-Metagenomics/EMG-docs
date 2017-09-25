Glossary
========

.. glossary::

    Study
        represents a collection of :term:`samples<sample>` and experiments applied to these :term:`samples<sample>`.


    Sample
        is a representation of the physical amount of material collected. It represents a specimen of a :term:`biome`. 


    Run
        the sequence file obtained from performing an experiment (an experiment generally includes several steps such as filtration, metatranscriptomic extraction and Illumina MiSeq sequencing, for example) on all or part of a :term:`sample`. Several runs can therefore be generated from a single :term:`sample`.


    Analysis result
        is the end result of the :term:`pipeline` analysis of a :term:`run`.


    Biome
        an ecological community type. in EBI Metagenomics, :term:`biomes<biome>` are organised hierarchically going from large types (such as soil, host-associated or aquatic) to more precise types (such as forest soil, skin or coastal) based on the `GOLD classification <https://gold.jgi.doe.gov/distribution#Classification>`_


    Pipeline
        a prescribed set of succesive steps needed to transform an input (raw reads for EBI Metagenomics) into an output with added information (annotated files with taxonomy and functional assignments for EBI Metagenomics) pipeline tool	a software or script used during the individual step of an analysis pipeline.


    Go Term
        is a defined vocabulary term to represent the functional attributes of a protein. Fine by the the `Gene Ontology <http://www.geneontology.org/>`_ initiative, GO terms are organised hierarchically to unambiguously define the biological process, precise molecular function and cellular location of a protein.


    Go slim
        terms are cut-down version of the GO hierarchy to be able to give an overview of the functional results. It is used on EBI Metagenomics website. The GO slim hierarchy lacks the fine granularity of the full GO hierarchy.


    InterPro
        combines protein signatures from a number of member databases into a single searchable resource, capitalising on their individual strengths to produce a powerful integrated database and diagnostic tool.
