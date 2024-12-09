Race track
==========

.. toctree::
   :maxdepth: 1
   :hidden:

   racetrack/material
   racetrack/roadmarkings
   racetrack/trafficsigns
   racetrack/otherelements
   racetrack/localization

* :doc:`Material </data/racetrack/material>`

  - Display of material characteristics

* :doc:`Road markings </data/racetrack/roadmarkings>`

  - The road markings on the track, their size and some other technical details. 

* :doc:`Traffic signs <racetrack/trafficsigns>`

  - The traffic signs PDF and the 3d model of the poles. 

* :doc:`Other elements on racetrack <racetrack/otherelements>`

  - Other elements on the track, like semaphores, pedestrian, blocks, etc.

* :doc:`Localization system replica <racetrack/localization>`

  - The description of our localization system, which you can use in order to create your own.


**Tracks**

Here you can find the maps in svg formats and extract all dimensions that are not specified in the following steps, or use the files to create your own track. 

    - `Test-track <https://github.com/ECC-BFMC/Documentation/blob/master/source/racetrack/Track_Test.svg>`_  
    - `Race-track <https://github.com/ECC-BFMC/Documentation/blob/master/source/racetrack/Track.svg>`_   


**Elements positioning**

The corresponding elements are placed in those areas, and won't be moved:
  - Start Semaphore at start. 
  - Parking sign at the beginind and at the end of the parking on left&right. 
  - Traffic lights at each entry of the specified intersection. 
  - Roundabout sign at each entry of the roundabout. 
  - Highway entry at each entry of the Highway.
  - Higway exit at each exit of the Highway.
  - Crosswalk sign at each crosswalk.
  - Tunnel

.. image:: ../images/racetrack/Track.png
   :align: center
   :width: 50%