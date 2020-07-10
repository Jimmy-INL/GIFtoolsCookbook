.. _comprehensive_workflow_dcip_index:


Comprehensive Workflows: DC and IP
==================================

.. .. figure:: images/title_page.png
..     :align: center
..     :width: 700

Here, we present a general workflow for loading, interpreting and inverting directed current resistivity (DC) and induced polarization (IP) data. We begin with UBC-GIF formatted data files for the DC and IP data. However, instruction is given in the case the data are in XYZ format. Our goal is to invert the data to recover both a 3D conductivity model and a 3D chargeability. You may work with the tutorial dataset provided or your own data:

    .. - `Download the tutorial data <https://github.com/ubcgif/GIFtoolsCookbook/raw/master/assets/comprehensive_tutorial_mt.zip>`_


.. These data were acquired from a `Geoscience Australia public database <https://data.gov.au/dataset/ds-ga-b20cdc13-039f-4217-b154-9d6e01208054/details?q=>`__ . We would like to acknowledge Geoscience Australia and Geological Survey of Queensland for allowing us to use this dataset to complete the tutorial. To reduce computation time and memory requirements, we have chosen to start with a subset of the original dataset.

This workflow is organized as follows:

.. toctree::
    :maxdepth: 1

    - Understanding DC and IP anomalies <1_basic_anomalies>
    - Loading 3D DC/IP data and cursory interpretation <2_load_data>
    - Assigning uncertainties <3_uncertainties>
    - Create, run and load 2D DC and IP inversion <4_local_2D>
    - Analyze 2D DC and IP inversion results <5_local_2D_results>
    - Batch 2D DC and IP inversion <6_batch_2D>
    - OcTree mesh design <7_octree>
    - Weights and reference model for DC octree inversion <8_dc_prep>
    - Setting appropriate parameters and running the DC inversion <9_dc_inv>
    - Examining convergence, data misfit and the recovered conductivity model <10_dc_results>
    - Weights and reference model for IP octree inversion <11_ip_prep>
    - Setting appropriate parameters and running the IP inversion <12_ip_inv>
    - Examining convergence, data misfit and the recovered chargeability model <13_ip_results>

 