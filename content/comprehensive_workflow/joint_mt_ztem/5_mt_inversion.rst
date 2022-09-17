.. _comprehensive_workflow_mt_ztem_5:

Independent MT Inversion
========================

For independent MT inversion, a standard approach for mesh design, creating interface weights, setting up and running the inversion, and analyzing the results was covered in the Cloncurry MT comprehensive workflow. We strongly urge the reader to be familiar with this material, as we will take the same approach here. For reference, visit:

    - :ref:`Designing an OcTree mesh <comprehensive_workflow_mt_5>`

    - :ref:`Interface weights, setting up and running the inversion <comprehensive_workflow_mt_6>`

    - :ref:`Analyzing inversion results <comprehensive_workflow_mt_7>`


Mesh Design
-----------

According to the apparent resistivity maps and sounding curves, the Earth is more conductive near the surface and more resistive at depth. Over the range of frequencies we are inverting (8 - 756 Hz), the apparent resistivities are generally between 100 - 1000 :math:`\Omega m`. From the skin depth formula:

	- :math:`\delta_{min}` = 200 m
	- :math:`\delta_{max}` = 5000 m

Here, we create an OcTree mesh using the E3DMT v2 utility. The steps are as follows:

    - :ref:`create OcTree mesh with E3DMT v2 utilities <createE3DMTv2octreeMesh>`

Once you have created the object, complete the following steps:

	1) Set the data object corresponding to the survey
	2) Define the mesh using *Edit Options*
	3) Run the utility
	4) Load results

For the field data provided, the following parameters we set in *Edit Options*.

.. figure:: images/mesh_parameters_mt.png
    :align: center
    :width: 500


Interface Weights
-----------------

Interface weights were generated to enforce lateral smoothness within the top few layers. For the tutorial MT data, we did the following:

    - :ref:`Create and interface weights utility <createinterfWeights>`
    - Use :ref:`edit options <utilEditOptions>` and set the following parameters:

        - set the OcTree mesh
        - set as *log model*
        - set topography as the active cells model
        - set number of layers and corresponding weights. Choose something exponentially decreasing. We chose 50, 20 and 5
        - Face value = 0.01
        - Face tolerance = 0.01

    - :ref:`Run the utility <utilRun>`
    - :ref:`Load results <utilLoadResults>`


Setup and Run Inversion
-----------------------

The MT inversion was carried out using E3DMT v2. There steps were as follows: 

    - :ref:`Create E3DMT v2 inversion object <createMTZTEMInv>`
    - Use edit options for :ref:`v2 <invEditOptions_e3dmt_ver2>` to set the inversion parameters
    - Click *Apply and write files*
    - :ref:`Run the inversion <invRun>`

For the tutorial dataset provided, the parameters used to invert the data are shown below.

.. figure:: images/inv_parameters_mt.png
    :align: center
    :width: 700

    Parameters used to invert the field dataset using E3DMT v2.



Analysis of Results
-------------------

Convergence
^^^^^^^^^^^

Once the inversion has finished:

	- :ref:`View convergence <convergence_curve>`

The Tikhonov curve for our tutorial inversion is shown below. According to the figure:

	- the total misfit (not data misfit) does not reach the target (chi-factor of 0.5) before the maximum number of beta iterations allowed (we set this to 10 in the input file). Thus the algorithm finished because a maximum number of iterations were completed.
	- the Tikhonov curve starts to flatten out around after the 8th iteration, indicating the point on the Tikhonov curve after which recovered models start to over-fit the data.
	- The **data misfit** at 8th iteration corresponds to a chi factor of 0.4. Therefore, we have likely over-estimated the global level of uncertainty on our data. If estimated correctly, we would expect the convergence curve to flatten our near a chi-factor of 1.


.. figure:: images/convergence_mt_002.PNG
    :align: center
    :width: 700

Data Misfit
^^^^^^^^^^^

Now that we have selected an iteration (or range of iterations) that we feel explains the data without overfitting:

    - :ref:`Load inversion results for these iterations <invLoadResults>`


According the Tikhonov curve, the recovered model at iteration 8 has a good chance of explaining the data without fitting the noise.

**Off-Diagonal Components:**

The observed data, predicted data and normalized misfits for off-diagonal impedance data are shown below at 80 Hz. From these plots, and plots at other frequencies, we found that:

	- The range of normalized misfits is more or less the same for all off-diagonal components and for all frequencies.
	- There were a few higher misfits at several locations, but they were not observed over all frequencies. So no coherent artifacts.


.. figure:: images/misfit_mt_off_diag.png
    :align: center
    :width: 700

    Observed data, predicted data and normalized misfit for all off-diagonal impedance components at 80 Hz. For each component, predicted and observe data are plotted on the same scale. All normalized misfit maps are plotted on a range from -1 to 1.


**Diagonal Components:**

The observed data, predicted data and normalized misfits for diagonal impedance data are shown below at 80 Hz. From these plots, and plots at other frequencies, we found that:

	- The range of normalized misfits is more or less the same for all diagonal components and for all frequencies.
	- No notable coherent artifacts in the misfit maps
	- The range of normalized misfits is the same as the off-diagonal components, indicating we are fitting diagonal and off-diagonal components evenly.



.. figure:: images/misfit_mt_diag.png
    :align: center
    :width: 700

    Observed data, predicted data and normalized misfit for all diagonal impedance components at 80 Hz. For each component, predicted and observe data are plotted on the same scale. All normalized misfit maps are plotted on a range from -1 to 1.


Recovered Model
^^^^^^^^^^^^^^^

The conductivity model recovered at the 8th iteration is shown below. The colormap was scaled to 1e-4 S/m to 0.25 S/m. According to the recovered model:

	- The basement is highly resistive.
	- The regional conductivity is higher in the Northeast and Southwest, with a larger-scale resistive feature trending from Northwest to Southeast. This is consistent with our original interpretation of the ZTEM data using total divergence maps.
	- Within the resistive feature are localized cluster of conductors.


.. figure:: images/model_mt_iter8.png
    :align: center
    :width: 700

    Recovered model at iteration 8.

