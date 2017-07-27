------------------------------------
Data flow from submission to results
------------------------------------

The graph below summarize the EBI Metagenomics data flow from submission to analysis results:

.. figure:: images/submit_graph_08_web031.png
   :scale: 50 %
.. https://stackoverflow.com/questions/12297493/why-does-image-scale-not-work-in-restructuredtext-when-generating-html-files   
**(1) Submissions are handled by the** `European Nucleotide Archive (ENA) <http://www.ebi.ac.uk/ena/>`_ **and therefore users have to have an ENA** `Webin account <https://www.ebi.ac.uk/ena/submit/sra/#registration>`_ .

   In addition, users submitting private data have to provide an expressed agreement that EBI Metagenomics can access their data for analysis, as described `here <https://www.ebi.ac.uk/metagenomics/submission>`_. Otherwise, we will not be able to access their data. EBI Metagenomics will, of course, handle these data confidentially.

**(2) Access to the** `ENA submission page <https://www.ebi.ac.uk/ena/submit/sra/#home>`_ **requires login in using a registered email address or a Webin identifier (Webin-XXXX).**

**(3 and 4): upload and submission.**

   These steps are described in details in the :ref:`ENA online guides`. EBI Metagenomics is providing a step by step guide to submission (:ref:`EBI Metagenomics online tutorials`. Please also check our `FAQs <https://github.com/ProteinsWebTeam/EMG-docs/blob/master/docs/faqs.rst>`_. 

   *Note that all queries concerning data submission should be directed to* `ENA dedicated help desk <mailto:datasubs@ebi.ac.uk>`_

   Following completion of these two steps, and after data validation by ENA, we will be able to access the submitted data and they will be queued for analysis (more details `here <https://github.com/ProteinsWebTeam/EMG-docs/blob/master/docs/analysis.rst>`_).

   The length of time requires for analysis varies according to the number of projects in the queue, the nature and the number of runs in the submission however we aim to have most analysis completed in less than a week once validated by ENA.

**(5) Upon completion of analysis, data will be uploaded on the website**

   EBI Metagenomics pipeline will generate a number of charts and downloadable files (fully described :ref:`Files available to download on the EBI Metagenomics website`.

**(6) For private data, users will have to login on the EBI Metagenomics website to access their data until they become public**

**(7) Private data will become public after an intital confidential period of two years.**
Submitters will receive an email from ENA prior to public release giving them the opportunity to extend the confidential period which is set to two years per default (as indicated at :ref:`Can I change the release date of my project?`).
and you can try here_.

.. _here: <http://emg-docs.readthedocs.io/en/latest/faqs.html#can-i-change-the-release-date-of-my-project>
