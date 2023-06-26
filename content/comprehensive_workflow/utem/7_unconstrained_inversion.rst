.. _comprehensive_workflow_utem_7:

Unconstrained Voxel Inversion
=============================

Here, we carry out a voxel TEM inversion using the mesh created on the :ref:`mesh design <comprehensive_workflow_utem_6>` page of the tutorial.
We provide the steps for setting up and running an inversion with TDRH v2. We then discuss some important aspects of choosing inversion parameters.

As was discussed on the :ref:`mesh design <comprehensive_workflow_utem_6>` page of the tutorial, the conductivities within the survey region for the **tutorial data** span many orders of magnitude. and it is unlikely the mesh generated 1) has small enough cells to model TEM responses from the plate targets accurately, and 2) has a total number of cells small enough for the inversion to be computationally feasible. Nonetheless, valuable insight will be gained by performing the inversion and used to direct future research.

Data Preparation
^^^^^^^^^^^^^^^^

For our final processing step, we downsample every data object we want included in the inversion based on the minimum station spacing used to generate our mesh. One again, we use

	- :ref:`Down-sample based on distance <objectDataDownsample>`.

**For the tutorial data,** a minimum station spacing of 111 m was used. We have 3-component data collected for 3 transmitter loops; 9 data objects total.
These data objects DO NOT need to be merged prior to inversion.

Inversion Parameters
^^^^^^^^^^^^^^^^^^^^

We can now invert surface UTEM data using TDRH v2.

    - :ref:`Create TDRH v2 inversion object <createTEMInv>`
    - Use :ref:`edit options <invEditOptions_td_ver2>` to set the inversion parameters
    - Click *Apply and write files*
    - :ref:`Run the inversion <invRun>`

For the tutorial data, we chose to invert using TDRH v2, as this code defines the physics in a universally right-handed coordinate system and is capable of inverting secondary field data.


.. figure:: images/inv_parameters.png
    :align: center
    :width: 500


.. note:: The parameters chosen for inversion of the field dataset were experimentally derived. The numbers used here worked well for inverting this dataset but should not necessary be used as general default values!

**Regarding beta cooling schedule:**

For synthetic modeling, we know the uncertainties on our data. With real data, we cannot be 100% sure that we have correctly estimated the uncertainties. In the case that we have globally under-estimated our uncertainties, we sometime set the *chi factor* to be less than 1. That way, we get to see more of the Tikhonov curve.

When setting the cooling schedule for the tutorial data set, the strategy was pretty straight-forward:

    - **beta max = 0.1**. The model recovered at the first iteration should clearly underfit the data. However if *beta max* is too large, you will have multiple iterations where the model doesn't budge because no emphasis is being put on fitting the data. We knew a good starting beta for the final inversion from cursory inversions of the data.
    - **beta min = 1e-7**. This can be set quite low. But it is good for the inversion to terminate within a reasonable number of beta iterations if target misfit is not reached.
    - **reduction factor = 0.25:** Generally we choose a value between 0.1 and 0.9. If the reduction factor is too large, the code will run for a long time since the reduction in beta at each iteration is small. If the reduction factor is too small, we do not get much detail regarding the convergence of the inversion.
    - **chi factor = 1** Here, we assume that appropriate uncertainties are set on the data. Thus, we assume the recovered model explains the data without over-fitting (fitting the noise) when the data misfit equals the number of data observations (chi factor = 1). In practice, you may choose a chi factor less than 1. This will allow you to get a better understanding of the convergence, especially if you have over-estimated the uncertainties.

**Regarding the alpha parameters:**

As a default setting, we frequently let :math:`\alpha_x = \alpha_y = \alpha_z = 1` and we let :math:`alpha_s = 1/dh^2` ; where :math:`dh` is the width of the smallest cells in the mesh. This effectively balances the emphasis on recovering a model that is similar to a reference model and recovering a model that has sufficient structure. If we have high confidence in our reference model, we may choose to increase :math:`\alpha_s` relative to :math:`\alpha_x`, :math:`\alpha_y` and :math:`\alpha_z`. If we have low confidence in our reference model, we may choose to decrease :math:`\alpha_s` relative to :math:`\alpha_x`, :math:`\alpha_y` and :math:`\alpha_z`

For this exercise, we have been provided with zero prior information regarding the Earth's structure or its electrical conductivity. We have assumed the background conductivity is 0.001 S/m but at no point have we validated this assumption. As a result, we have set :math:`\alpha_s = 10^{-10}` and let :math:`\alpha_x = \alpha_y = \alpha_z = 1`. This will recover a conductivity model which is primarily driven by the data, and is impacted minimally by the reference model.

**Regarding the background, starting and reference models**

For the background, starting and reference models, we chose 0.001 S/m. This value was suggested by a 2D ZTEM study that came with the original dataset. Before you choose these values for your project, there are some things you should consider.

If you choose a background conductivity that is lower than the true conductivity:

    - The overall range of conductivities in the recovered model may be lower than the true range of conductivities.
    - Your inversion will be more sensitive to structures at depth. Recovered conductors may be lower conductivity and placed at larger depths.

If you choose a background conductivity that is higher than the true conductivity:

    - The overall range of conductivities in the recovered model may be higher than the true range of conductivities.
    - Your inversion will be not but as sensitive to structures at depth. Recovered conductors may highly conductive and placed at shallower depths.


Inversion Outputs
^^^^^^^^^^^^^^^^^


.. figure:: images/convergence.png
    :align: center
    :width: 400




.. figure:: images/inv_unconstrained.png
    :align: center
    :width: 700





.. C:\Users\devin\anaconda3
.. C:\Users\devin\anaconda3\Library\mingw-w64\bin
.. C:\Users\devin\anaconda3\Library\usr\bin
.. C:\Users\devin\anaconda3\Library\bin
.. C:\Users\devin\anaconda3\Scripts
