.. _comprehensive_workflow_mtztem_index:


Comprehensive Workflows: Joint MT/ZTEM
======================================

**Author: Devin C. Cowan**

**Published: October, 2022**


Here, we present a general workflow for loading, interpreting, and jointly inverting Magnetotelluric (MT) and Z-axis Tipper electromagnetic (ZTEM) data. Our goal is to recover a single 3D conductivity model which explains both datasets. **We assume the reader is already familiar with comprehensive workflows that process and invert MT and ZTEM data separately** ; see :ref:`MT comprehensive workflow <comprehensive_workflow_mt_index>` and :ref:`ZTEM comprehensive workflow <comprehensive_workflow_ztem_index>` . This workflow focussed primarilly on joint inversion. However, we will link to relevant portions of the aforementioned workflows when necessary.

You may work with the tutorial dataset provided or your own data:

    .. - `Download the tutorial data <https://github.com/ubcgif/GIFtoolsCookbook/raw/master/assets/comprehensive_tutorial_ztem.zip>`_


**Something about where the data came from**

.. The data used for this tutorial were collected at Dufferin Lake as part of a uranium exploration project. The data are public domain. They were downloaded from the `Saskatchewan Mineral Assessment Database <https://www.saskatchewan.ca/business/agriculture-natural-resources-and-industry/mineral-exploration-and-mining/saskatchewan-geological-survey/saskatchewan-mineral-assessment-database-smad>`__ . The original data have been down-sampled to make the size of data files more manageable.


.. .. figure:: images/title_page.png
..     :align: center
..     :width: 700


**Tutorial Sections**

.. toctree::
    :maxdepth: 1

    - Understanding MT and ZTEM anomalies <1_basic_anomalies>
    - Loading geophysical data and transforming to GIF convention <2_load_data>
    .. - Standard assignment of uncertainties to ZTEM data <3_uncertainties>
    .. - Preparing data for inversion within the GIFtools framework <4_data_preparation>
    .. - Mesh design <5_mesh_design>
    .. - Setting appropriate parameters and running the inversion <6_inversion>
    .. - Examining convergence, data misfit and the recovered model <7_results>

 