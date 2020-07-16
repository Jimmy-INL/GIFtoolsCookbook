.. _comprehensive_workflow_dcip_6:

.. include:: <isonum.txt>

Batch 2D Inversion
==================

The user may choose to assign distinct uncertainties to each line of 2D DC/IP data and invert the respecitve lines independently. If the same set of parameters is to be used for each DC/IP line however, the inversions can be run as part of a batch. The batch inversion works well if 1) you have run test inversions on one or more survey lines and, 2) both the uncertainties and chi-factor are reasonable. Here, we demonstrate how to run a batch inversion for all DC and IP survey lines.


2D DC Batch Inversion
---------------------

Defining an Inversion Template
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Here, we define the parameters that will be used when inverting each survey line. To create the template:

    - :ref:`Create a new 2D DC inversion object <createDCIPInv>` and select a working directory when prompted. It is important that you create a new inversion object for this.
    - Use :ref:`edit options <invEditOptions_dcip2d>` to set the parameters for the inversion. For the tutorial data, we used the :ref:`same parameters as before <comprehensive_workflow_dcip_4_DC>`.
    - Click *Apply*. **Do not** write the files.

.. note::

    - You will need to enter placeholders for the data and topography, but they will be ignored during the batch inversion.
    - If you are confident in your misfits and chi-factor, use the *Discrepancy* option when defining the trade-off parameter.


Performing the Batch Inversion
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To set up and run the batch inversion, apply the following under the *Batch Inversion* menu:

    - :ref:`Set inversion template <batchInversionSetTemplate>` to the 2D DC inversion object you created
    - :ref:`Set the 2D DC data objects <batchInversionSetData>` (the data object for each survey line). If applicable, GIFtools will prompt you to select the associated topography objects.
    - :ref:`Create/Write all <batchInversionCreateInv>` 2D inversion objects. **If** sensitivity weighting are being applied, GIFtools will automatically compute the sensitivity weights. Please allows this step to finish before doing anything else.
    - :ref:`Run inversions <batchInversionRun>`


Results
^^^^^^^

If the **Default** option was selected for the trade-off parameter, the user believes the target chi-factor for each survey line could be different. For each 2D inversion object, the user must:

    - Analyze the inversion results and choose a final model according to the :ref:`Analyzing 2D Inversion Results <comprehensive_workflow_dcip_5>` section of this tutorial. **For the tutorial data**, in order (lines 1-10), we chose iterations: 12, 12, 13, 12, 12, 11, 11, 10, 10 and 11.

If the **Discrepancy** option was used and a target chi-factor was defined, you can use functionality under the *Batch Inversion* menu to:

    - :ref:`Load the final model or the first to reach the target chi-factor <batchInversionLoad>` for all 2D inversions.



Interpolation to 3D Mesh
^^^^^^^^^^^^^^^^^^^^^^^^

Once you have completed the batch inversion, it is benefitial to compare the set of recovered 2D models side by side. Here, we interpolate the set of recovered 2D models onto a 3D tensor mesh. We start by creating a 3D tensor mesh. Next, we interpolate the set of 2D models onto the 3D mesh.

**Creating the mesh:**

    - :ref:`Create 3D tensor mesh <create_mesh_3D>`

        - Use the 3D DC data object to calculate limits of the core mesh region
        - Make any adjustments to parameters
        - Click *OK*


The set of parameters used to create a 3D mesh for the **tutorial data** is shown below.

.. important::

    The user is strongly urged to:

        - Set *dx* and *dz* to match the values used for constructing the 2D mesh. And let *dx* = *dy*.
        - Remove any padding unless it is important for interpretation.



.. figure:: images/mesh3D.png
    :align: center
    :width: 500

    Parameters used to create 3D tensor mesh.


Once the 3D mesh has been created, select any of the *Batch Inversion* objects and:

    - :ref:`Merge all <batchInversionMerge>` to interpolate to 3D mesh.


**For the tutorial data**, we see the set of recovered 2D conductivity models below. For comparison, we also show the result if *Discrepancy* and a chi-factor of 1 was used to define the trade-off parameter.


.. figure:: images/inv_dc2d_batch.png
    :align: center
    :width: 600

    2D conductivity models with *Default* trade-off parameter and manual picking (left). 2D conductivity models with *Discrepancy* and a chi-factor of 1 (right).



2D IP Batch Inversion
---------------------


The process for creating and running a 2D IP batch inversion is nearly identical to that of a 2D DC batch inversion. When prompted, the batch inversion will ask you for the associated set of 2D DC inversion objects. This is done to assign a background conductivity model for each IP inversion.

**For the tutorial data**, the 5th iteration was chosen as the final model for all survey lines. The set of recovered 2D models was interpolated to the same 3D mesh. We see the set of recovered 2D chargeability models below. For comparison, we also show the result if *Discrepancy* and a chi-factor of 1 was used to define the trade-off parameter.



.. figure:: images/inv_ip2d_batch.png
    :align: center
    :width: 600

    2D chargeability models with *Default* trade-off parameter and manual picking (left). 2D chargeability models with *Discrepancy* and a chi-factor of 1 (right).

