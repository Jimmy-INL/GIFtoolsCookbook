.. _comprehensive_workflow_utem_8:

Voxel Inversion Results
=======================

Here, we demonstrate a common practice for examining the output of the inversion code. This includes examining the convergence, the data misfit and the recovered model. Before looking at recovered models, the user is strongly urged to examine the convergence of the algorithm first (Tikhonov curve). By examining the convergence, we can:

    - determine if our data is in UBC-GIF data convention. The data misfit will be large and will not reduces at each iteration otherwise
    - see if the inversion is able to reach target misfit
    - infer whether the target misfit is reasonable; i.e. did we globally over or under-estimate the uncertainties on our data

We then assess how well a given recovered model explains the data by looking at the predicted data, observed data and normalized data misfit maps. From this we can determine whether:

    - the predicted data fits the amplitude, shape and character of observed anomalies for each component and for each frequency
    - the estimated uncertainties were reasonable for each component and for each frequency.
    - the inversion must be re-run with a new set of uncertainties

Only when the convergence and data misfit are acceptable can we infer geological structures from recovered models.

.. important:: As was discussed on the :ref:`mesh design <comprehensive_workflow_utem_6>` page of the tutorial, the conductivities within the survey region for the **tutorial data** span many orders of magnitude. and it is unlikely the mesh generated 1) has small enough cells to model TEM responses from the plate targets accurately, and 2) has a total number of cells small enough for the inversion to be computationally feasible. Nonetheless, valuable insight will be gained by performing the inversion and discussing the results.

Convergence
^^^^^^^^^^^

Once the inversion has finished:

    - :ref:`View convergence <convergence_curve>`

The Tikhonov curve for our tutorial inversion is shown below. At about the 4th iteration, the decrease in 


.. figure:: images/convergence.png
    :align: center
    :width: 400


.. note:: There is a bug in the subroutine that computes and outputs the model norm when topography is included. This bug DOES NOT impact the recovered model and is currently being fixed.


Data Misfit
^^^^^^^^^^^




Recovered Model
^^^^^^^^^^^^^^^







.. figure:: images/inv_unconstrained.png
    :align: center
    :width: 700


