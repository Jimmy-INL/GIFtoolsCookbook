.. _comprehensive_workflow_dcip_6:

.. include:: <isonum.txt>

Batch 2D Inversion
==================

The user may choose to assign distinct uncertainties to each line of 2D DC/IP data and invert the respecitve lines independently. If the same set of parameters is to be used for each DC/IP line, the inversions can be run as part of a batch. The batch inversion works well if 1) you have run test inversions on one or more survey lines and, 2) both the uncertainties and chi-factor are reasonable. Here, we demonstrate how to run a batch inversion for all DC and IP survey lines.


2D DC Batch Inversion
---------------------

Defining an Inversion Template
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^






Running the Batch Inversion
^^^^^^^^^^^^^^^^^^^^^^^^^^^




Results
^^^^^^^


.. figure:: images/inv_dc2d_batch.png
    :align: center
    :width: 600

    Batch inversion results.




2D IP Batch Inversion
---------------------

Defining an Inversion Template
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^




Running the Batch Inversion
^^^^^^^^^^^^^^^^^^^^^^^^^^^




Results
^^^^^^^


.. figure:: images/inv_ip2d_batch.png
    :align: center
    :width: 600

    Batch inversion results.


Interpolation to 3D Mesh
------------------------