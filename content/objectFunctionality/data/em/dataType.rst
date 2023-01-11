.. _objectEMdtype:

.. include:: <isonum.txt>

EM Data Type Functionality
==========================



.. _objectEMdtype_EM3Dsounding_tx:

Defining Transmitters (3D EM and sounding data)
-----------------------------------------------

For ``FEM3Ddata``, ``FEM3Dsounding``, ``TEM3Ddata`` and ``TEM3Dsounding`` data objects, we can define transmitters for the survey.
This functionality is accessed using the drop-down menu:

**"data type menu"** |rarr| **Add Transmitters**




.. _objectEMdtype_EM3Dsounding_tx_airborne:

Create Surface/Airborne Sources
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Create inductive sources (loops) for surface or airborne EM surveys. This functionality is accessed using the drop-down menu:

**"data type menu"** |rarr| **Add Transmitters** |rarr| **Create Surface/Airborne Sources**




.. _objectEMdtype_EM3Dsounding_tx_surface:

Create Single Inductive/Galvanic Source
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Create a single inductive or galvanic source for all data in the object. This functionality is accessed using the drop-down menu:

**"data type menu"** |rarr| **Add Transmitters** |rarr| **Create Single Inductive/Galvanic Source**



.. _objectEMdtype_EM3Dsounding_rx:

Defining Receivers (3D EM and sounding data)
-----------------------------------------------

For ``FEM3Dsounding`` and ``TEM3Dsounding`` data objects, we can define receivers for the survey.
This functionality is accessed using the drop-down menu:

**"data type menu"** |rarr| **Add Receivers**



.. _objectEMdtype_EM3Dsounding_rx_airborne:

Create Surface/Airborne Receivers
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Create loop receivers for surface or airborne EM surveys. This functionality is accessed using the drop-down menu:

**"data type menu"** |rarr| **Add Transmitters** |rarr| **Create Surface/Airborne Receivers**



.. _objectEMdtype_removeTx:

Remove Transmitters
-------------------

This functionality allows the user to remove transmitter information from the data object.

Select the object and the menu **"data type menu"** |rarr| **Remove transmitters**


.. _objectEMdtype_removeRx:

Remove Receivers
----------------

This functionality allows the user to remove receiver information from the data object.

Select the object and the menu **"data type menu"** |rarr| **Remove receivers**




.. _objectEMtype_waveform:

Waveform (TDEM objects only)
----------------------------

Here, we describe functionality related to defining, viewing and exporting waveforms for TEM data objects. This functionality is accessed through:

**data type menu** |rarr| **Waveform**


.. _objectEMtype_waveform_exp:

Create Exponent On - Ramp Off
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Here, the user defines an exponential ramp-on linear ramp-off waveform and sets it to the selected TEM data object. This functionality is accessed through:

**data type menu** |rarr| **Waveform** |rarr| **Create exponent on; ramp off**

The parameters defining this waveform are as follows:

    - **minimum time:** the starting time for the waveform (in seconds). This time **must** be before your first time channel
    - **maximum time:** the end time for the waveform (in seconds). This time **must** be after your latest time channel
    - **time = 0:** the shut-off time
    - **Number of segments:** Number of intervals after t0 which use a different time-step length
    - **Samples per segment:** Number of linearly sampled points which define the time-step length in each segment
    - **Exponent slope:** The constant :math:`\alpha` defining the exponential ramp on
    - **Exponent time:** The duration of the exponential ramp on
    - **Number of exp samples:** Number of data points, linearly sampled, defining the waveform during the exponential ramp on
    - **Ramp time:** The duration of the linear ramp off
    - **Number of ramp samples:** Number of data points, linearly sampled, defining the waveform during the linear ramp off



.. _objectEMtype_waveform_stepoff:

Create Step Off
^^^^^^^^^^^^^^^

Here, the user defines a step-off waveform and sets it to the selected TEM data object. This functionality is accessed through:

**data type menu** |rarr| **Waveform** |rarr| **Create step off**

The parameters defining this waveform are as follows:

    - **minimum time:** the starting time for the waveform (in seconds). This time **must** be before your first time channel
    - **maximum time:** the end time for the waveform (in seconds). This time **must** be after your latest time channel
    - **time = 0:** the shut-off time
    - **Number of segments:** Number of intervals after t0 which use a different time-step length
    - **Samples per segment:** Number of linearly sampled points which define the time-step length in each segment



.. _objectEMtype_waveform_import:

Import a Waveform
^^^^^^^^^^^^^^^^^

Here, the user imports a custom waveform from a text file and sets it to the selected TEM data object. This functionality is accessed through:

**data type menu** |rarr| **Waveform** |rarr| **Import (3D format)**


.. _objectEMtype_waveform_view:

View
^^^^

Here, the user may look at the waveform assigned to the selected TEM data object. This functionality is accessed through:

**data type menu** |rarr| **Waveform** |rarr| **View**

.. _objectEMtype_waveform_1D:

Export for 1D
^^^^^^^^^^^^^

Here, the user may export the waveform in the format used by the EM1DTM code. This functionality is accessed through:

**data type menu** |rarr| **Waveform** |rarr| **Export for 1D**


.. _objectEMtype_waveform_3D:

Export for 3D
^^^^^^^^^^^^^

Here, the user may export the waveform in the format used by 3D codes. This functionality is accessed through:

**data type menu** |rarr| **Waveform** |rarr| **Export for 3D**
