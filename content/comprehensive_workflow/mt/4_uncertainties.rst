.. _comprehensive_workflow_mt_4:


Assigning Uncertainties
=======================

Here, we provide a basic approach for assigning uncertainties to impedance data. The role of uncertainties in geophysical inversion is presented in the :ref:`fundamentals of inversion <Fundamentals_Uncertainties>`. When assigning uncertainties, we want to ensure we fit the anomaly and not the background. We also want to ensure we fit each component and frequency equally.

Percent Versus Floor Uncertainty
--------------------------------

**Off-Diagonal Impedances (ZXYR, ZXYI, ZYXR and ZYXI):**

For off-diagonal impedance tensor data (ZXYR, ZXYI, ZYXR and ZYXI), the range of data values is significantly different for each component and for each frequency. In general:

    - impedances at higher frequencies are larger in magnitude than impedances observed at lower frequencies.
    - off-diagonal impedance data values are non-zero unless there is significant 3D structure effects.

Therefore **the uncertainties applied to off-diagonal impedance data should be dominated by a percent**; as opposed to a floor which assigns equal uncertainty to all data values. Since the magnitude of the data is frequency-dependent, it is obvious we much assign frequency-dependent uncertainties. But what about balancing the uncertainties between each component? For this, we consider the apparent resistivity formula:

.. math::
    \rho_{app} = \frac{ \big | Z_{ij} \big |^{2} }{\omega \mu} \;\;\; \textrm{where} \;\;\; i \neq j


For a given frequency, this formula states that small :math:`Z_{xy}` and small :math:`Z_{yx}` values correspond to small apparent resistivities. So if you apply only a floor uncertainty to the impedance data, you would be over-fitting resistive structures and under-fitting conductive structures.


**Diagonal Impedances (ZXXR, ZXXI, ZYYR and ZYYI):**

Diagonal impedances are impacted by 3D effects. In the absence of 3D effects, the diagonal impedances are theoretically equal to zero. If you were to apply only a percent uncertainty to the data, you would over-fit the background values and under-fit the anomalies. Therefore, **the uncertainties applied to diagonal impedance data should be dominated by a floor**. For simple geologies:

    - ZXXR, ZXXI, ZYYR and ZYYI data at a particular frequency may span the same range of values. If not, you may need to apply a different floor to each component.
    - ZXXR, ZXXI, ZYYR and ZYYI data at each frequency may span the same range of values, respectively. If not, you may need to apply a different floor for each frequency.


.. note:: When the inversion is complete, we will be able to assess whether the estimated uncertainties on our data were correct. If not, the inversion will need to be re-run with a new set of uncertainties.


General Approach
----------------

**Off-Diagonal Impedances (ZXYR, ZXYI, ZYXR and ZYXI):**

It is common to apply uncertainties of 5% - 10% as a first estimate. You may choose to apply higher or lower percentages to different frequencies if you believe the data are more or less noisy, respectively. We may also add a very small floor to the uncertainties in the rare case there are data approximately equal to zero.

**Diagonal Impedances (ZXXR, ZXXI, ZYYR and ZYYI):**

There are a few options for choosing the floor uncertainty values for each component at each frequency:

    1) The user may take some fractional percents of the largest anomalous value and use that as the floor.
    2) The user may sort the data by absolute value, and choose a threshold at which the data values contain an insignificant amount of signal and are dominated by noise.

Since the diagonal impedances do less to constrain the inversion result than the off-diagonal components, it is best to over-estimate the uncertainties for ZXXR, ZXXI, ZYYR and ZYYI rather than to under-estimate the uncertainties. To ensure that off-diagonal impedances are driving the inversion, sometimes very large uncertainties are applied to the diagonal imdpedances.


.. figure:: images/Uncertainties_Approach_Floor.png
    :align: center
    :width: 700

    Option 1 for choosing uncertainties (left). Option 2 for choosing uncertainties (right).


To examine sorted data and apply uncertainties:

    - Use the :ref:`GUI for applying frequency-dependent uncertainties <objectAssignUncertGUI>`.


.. note:: To keep the tutorial example simple, we choose to add uncertainties of 0.02 + 20% to all diagonal impedances (ZXXR, ZXXI, ZYYR and ZYYI). And uncertainties of 0.0001 + 5% were added to all off-diagonal impedances (ZXYR, ZXYI, ZYXR and ZYXI).





