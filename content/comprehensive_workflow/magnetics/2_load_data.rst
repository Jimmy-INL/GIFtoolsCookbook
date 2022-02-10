.. _comprehensive_workflow_magnetics_2:

.. include:: <isonum.txt>

Loading TMI Data and Cursory Interpretation
===========================================

The first step in any project is to load field collected data and visualize it. Here, we load TMI data, assign and remove the background magnetic field, and visualize the TMI anomaly data.

**The tutorial data consists of both local and regional datasets**. The local scale dataset encompasses our region of interest. It consists of many North-South lines of surface TMI data collected on the back of a skidoo. The coarse-scale regional magnetic data was obtained from Natural Resources Canada. Regional data (if available) can be used to better understand regional-scale magnetic anomalies and constrain local inversion results. 


.. important:: Requires GIFtools v2.34 or later.

Starting Your Project
---------------------

    - Open GIFtools
    - :ref:`Set the working directory <projSetWorkDir>`


Import Files
------------

.. important:: If you are working with your own dataset and you do cannot acquire regional scale data, you can still complete this tutorial; although you will not be able to implement certain techniques.

Here, we import the TMI and topography datasets. **Local and regional tutorial data are in a general XYZ format but the same functionality is available for CSV or UBC-GIF formatted data**. To import the TMI data and topography:

    - :ref:`Import local and regional topography data (XYZ format) <importTopo>`. These files are called *topo_xyz_local.xyz* and *topo_xyz_regional.xyz*.
    - :ref:`Import local and regional TMI magnetic data (XYZ format) <importMagData>`. These files are called *mag_xyz_local.xyz* and *mag_xyz_regional.xyz*.


Defining Earth's Inducing Field
-------------------------------

.. note:: If the data file is UBC-GIF format, the file contains the properties for defining the Earth's field. And these properties are automatically assigned upon loading the data file.

In this step, we define the inclination, declination and intensity of the Earth's magnetic field for any magnetic data objects. There are several ways to obtain this information:

    - It is provided within the magnetic data file
    - The historical `international geomagnetic reference field <//en.wikipedia.org/wiki/International_Geomagnetic_Reference_Field>`__ for the survey location on the survey date is obtained using online resources
    - The data file contains columns defining the inclination, declination and field intensity for each survey point.

So long as the size of the survey region is reasonable, we assume the properties of the Earth's field are constant throughout the region. To assign the inclination, declination and intensity:

    - If inclination, declination and intensity columns are provided, :ref:`view statistics <viewData_statistics>` and determine the average values.
    - :ref:`Assign the field parameters <objectEditFieldParam>`

**For the local tutorial data**, we were provided with inclination, declination and field intensity columns. Using *view statistics* and taking the mean values, we obtained:

    - *intensity* = 58266 nT
    - *inclination* = 81.26 deg
    - *declination* = -28.44 deg

**Regional tutorial data supplied by NRCan** were processed and provided such that the anomaly corresponds to a survey carried out June 5th, 2020. This dataset also assumes a constant flight height of 305 m (elevation ~900 m). Using historical IGRF data from the `National Centers for Environmental Information <https://www.ngdc.noaa.gov/geomag/calculators/magcalc.shtml#igrfwmm>`__ , we obtained the following properties for the Earth's field at the regional scale:

    - *intensity* = 57363 nT
    - *inclination* = 80.24 deg
    - *declination* = -22.35 deg


.. note:: During the time between the collection of the local and regional datasets, the Earth's field may have change significantly. The impact this has on necessary processing is discussed later in the tutorial. 


Removing the Background Field
-----------------------------

The background field may be defined using base station measurements (which contain regional signals) or as the Earth's inducing field (which does not). We must remove the background field from the total field measurements in order to obtain the TMI anomaly data. There are two ways in which this can be done using GIFtools:

    - If the background field (base station or IGRF) is provided in a column, the :ref:`column calculator <objectCalculator>` can be used to subtract the background field from the total field.
    - Or use :ref:`remove IGRF <objectRemoveIGRF>` to subtract the inducing field defined in the previous step of the tutorial.

**For the local tutorial data**, we subtracted the Earth's field from the total field using the column calculator. As such, regional and local information are contained within the resulting data column.

**For the regional tutorial data**, the background field had already been removed and this step was not necessary.



Cursory Interpretation
----------------------

- To view the data, you may select any data object and :ref:`plot with VTK <viewData>`

**Local tutorial data:**

The topography and TMI anomaly data are shown below. The topography ranges from an elevation of 540 m to 670 m. The tutorial data were were collected at the surface. In this case, several extremely high amplitude signals were measured and the range of the color scale needed to be fixed between -2000 nT and 10000 nT. The general anomalies features observed in the data map appear to be trending from WSW to ENE. And a large anomalous structure is seen near the middle of the data map.

    
.. figure:: images/cursory_interpretation_local.png
    :align: center
    :width: 700


**Regional tutorial data:**

The topography, TMI anomaly data and coverage of the local survey data are plotted below. The WSW to ENE trending features in the local data is consistent with regional features. The background anomaly values observed in the local data are in fact associated with the 'lows' produced by larger scale features. And the regional data itself appears to be in the 'low' produced by even larger period signals; i.e. regional background values are negative. 

    
.. figure:: images/cursory_interpretation_regional.png
    :align: center
    :width: 700



Downsampling the Data
---------------------

The along-line sampling rate for both surface and airborne surveys is generally higher than is necessary to accurately characterize anomalies. Furthermore, 3D potential field inversions cannot fit the data if multiple data points lie above a single cell; implying you may consider some aspects of mesh design during this step. Here, we downsample the local magnetic data based on a desired minimum spacing; which is generally determined by the line separation.

    - :ref:`Downsample by distance <objectDataDownsample>`


**For the local tutorial data**, we downsampled to a minimum spacing of 25 m. This is roughly equal to half the average line spacing for the local magnetic survey. This reduced the total number of data points from 101,679 to 11,192. Downsampling to 25 m was able to greatly reduce the number of data without filtering out coherent higher frequency signals we are attributing to magnetized structures.

**The regional tutorial data** has already been gridded to a spacing of 200 m and does not need to be downsampled.

