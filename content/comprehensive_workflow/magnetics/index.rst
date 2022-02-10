.. _comprehensive_workflow_magnetics_index:


Comprehensive Workflows: TMI Magnetics
======================================

**Author: Devin C. Cowan**

**Published: March, 2020**


.. Here, we present a general workflow for loading, interpreting and inverting "University of Toronto ElecroMagnetometer" (UTEM) data. We begin with UTEM data in AMIRA TEM files. Our goal is to invert the data to recover a 3D conductivity model. You may work with the tutorial dataset provided or your own data:

..     - `Download the tutorial data <https://github.com/ubcgif/GIFtoolsCookbook/raw/master/assets/comprehensive_tutorial_ztem.zip>`_


.. The data used for this tutorial were collected at Dufferin Lake as part of a uranium exploration project. The data are public domain. They were downloaded from the `Saskatchewan Mineral Assessment Database <https://www.saskatchewan.ca/business/agriculture-natural-resources-and-industry/mineral-exploration-and-mining/saskatchewan-geological-survey/saskatchewan-mineral-assessment-database-smad>`__ . The original data have been down-sampled to make the size of data files more manageable.


.. .. figure:: images/title_page.png
..     :align: center
..     :width: 700


Tutorial Sections
-----------------

.. toctree::
    :maxdepth: 1

    - Understanding magnetic anomalies <1_basic_anomalies>
    - Loading data and cursory interpretation <2_load_data>
    - Equivalent source inversion <3_equivalent_source>
    - Upward continuation and reduction to pole <4_upward_continuation>
    - Polynomial detrending <5_detrending>
    - Data interpretation (including remanence) <6_data_interpretation>
    - Uncertainties for magnetic data <7_uncertainties>
    - Mesh design <8_mesh_design>
    - Regional inversion (optional) <9_regional_inversion>
    - Regional removal <10_regional_removal>
    .. - Setting appropriate parameters and running the inversion <6_inversion>
    .. - Examining convergence, data misfit and the recovered model <7_results>

 