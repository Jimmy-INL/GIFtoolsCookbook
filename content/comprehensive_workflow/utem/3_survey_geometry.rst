.. _comprehensive_workflow_utem_3:

Survey Geometry and Data Visualization
======================================

For UTEM, the representation of the data being inverted (field measurements) is not the same as the representation of the data used for interpretation (e.g. primary normalized, primary reduced, channel reduced). As such, we need a means of converting between the two. Except in the case of channel reduced data, this conversion requires that we know the primary field. 

Here, we define the survey geometry (source and receivers) for each data object and use it to compute the analytic primary field. We then demonstrate how total B-field measurements can be converted to representations used for plotting, and visa versa.


.. important:: Requires GIFtools v3.1 or later.


Defining the Survey Geometry
----------------------------

During the survey, it is common for practitioners to map the wire path of each transmitter loop with GPS and convert the values to UTM coordinates. The set of discrete wire segments defining the loop can be used to compute the primary field analytically according to the Biot-Savart law. The orientations of UTEM receivers are also collected. This information is especially important when field components are not necessary collected along the X, Y and Z directions.


Transmitters
^^^^^^^^^^^^

To define the transmitter for each data object, we:

    - use the :ref:`create single inductive/galvanic sources <objectEMdtype_EM3Dsounding_tx_surface>` functionality
    - select 'load text file'
    - find the XYZ file containing the nodes which define the loop and load; e.g. *wire_path_1501.txt*
    - the click 'OK'


.. important:: The XYZ file containing the nodes for the transmitter has **no headers**. And unlike topography files, the first line **is not** the number of nodes. Finally, the first and last line **must be the same** in order to close the loop and define an inductive source!


Receivers
^^^^^^^^^

To define the receivers for each data object, we:

    - use the :ref:`create surface/airborne sources <objectEMdtype_EM3Dsounding_rx_airborne>` functionality
    
**For the tutorial data:**

    - select 'square loop' and set the 'loop width' to 1 m. So long as the loop dimension is significantly smaller than the minimum cell size used to construct the mesh, we are effectively modeling the fields at a point.
    - set the 'loop path/integration path' to be 'Right-handed/CCW'. We will be inverting the data with the *TDRH octree v2* code, which uses a universally right-handed coordinate system.
    - since the tutorial data are defined along the X, Y and Z directions, and the bearing is left as 0 (Northing), within the 'Orientation' box:

        - Select 'Horizontal coplanar' to define X-component data
        - Select 'Vertical coaxial' to define Y-component data
        - Select 'Vertical coplanar' to define Z-component data



Computing the Primary Field
---------------------------

Now that we have defined the transmitter and receivers for all data objects:

    .. - :ref:`Compute Biot-Savart Primary Field<>`



Converting Field Data to UTEM Representations
---------------------------------------------






Visualization
-------------





