Embedded platform
=================

.. toctree::
   :maxdepth: 1
   :hidden:

   embeddedplatform/preliminarySetup
   embeddedplatform/buildAndFlash
   embeddedplatform/newComponent
   embeddedplatform/debugging
   embeddedplatform/mainFlow

* :doc:`Preliminary setup <embeddedplatform/preliminarySetup>`

  - You will need to follow this in order to set up your environment. 

* :doc:`This is how you can build your project <embeddedplatform/buildAndFlash>`

  - This is how you can build the project once the modifications are done.

* :doc:`Adding a new component (object) <embeddedplatform/newComponent>`

  - If you wish to add a new component, we have a script for it!

* :doc:`Debugging via serial <embeddedplatform/debugging>`

  - This is how you debug the board via serial

* :doc:`How it works <embeddedplatform/mainFlow>`

  - Some explanations regarding how the code works

The embedded platform refers to the code that is written on the Nucleo board, more precisely the low level application, which runs on the 
micro-controller Nucleo-F401RE. It aims to provide an interface between high level processing and low level motors control and sensor reading. The code 
uses mbed os version=6.17, and such, it's written in C/C++. 

The project is structured on 4 layers: Brain, Drivers, Periodics and Utils:
    - The 'Brain' folder contains the state machine of the Nucleo, the KL mannager and the power safety features, together with a file for global states defininition. More controlling methods can be handled here. 
    - The 'Drivers' folder contains the code to interact directly with the BatteryManager, BNO, SteeringMotor, SpeedingMotor, SerialCommunication, VelocityControlDuration.
    - The 'Periodics' folder contains the tasks that are executed periodically by the Nucleo board, such as IMU publishing values on serial, blinker to signal the running version, instant consumption publisher, the total voltage publisher, and ResourceMonitor.
    - The 'Utils' folder contains various working tools, such as the serial communication message construction/deconstruction, callbacks on the necessary functions, tasks interface and task manager.