Brain project
=============

.. toctree::
   :maxdepth: 1
   :hidden:

   brain/preliminarySetup
   brain/newComponent
   brain/running
   brain/mainFlow

- * :doc:`Preliminary setup <brain/preliminarySetup>`

  - You will need to follow this in order to set up your environment. 

- * :doc:`New component <brain/newComponent>`

  - This is how you can integrate new components in the code.

- * :doc:`Running the system <brain/running>`

  - This is how you start your code.

- * :doc:`How it works <brain/mainFlow>`

  - Some explanations regarding how the code works

As substitutes for this Brain project are the Startup_c and Brain_ROS. Though none of them are maintained, so if you chose to develop on each of them, you will 
have to adapt it based on the information you find here. 

This documentation describes the given brain project, which runs on the raspberry pi. It eases the 
process of starting up your vehicle by displaying some basic functionalities and describes 
how to use the given APIs to interact with the V2X systems. The following things are implemented
in the project (be advised that everything can be tunned to your project needs!):

    - Simple service-like architecture based on 4 Queues, each with a higher level of prioritization, where messages can be sent.
    - Example of parallel processes, each with different running threads. 
    - A class that describes all the messages, who's their owner and what their type is.
    - Subscription examples for certain messages
    - Gateway that handles all the sent messages and forwards them to the subscribers (to enable easy testing and developing).
    - A camera driver-like process that can also modify in real time some of the camera parameters (like ISO and aperture), send multiple images with different settings (like resolution) and enables easy camera recording functionality.
    - A serial communication driver-like process, that communicates with the Nucleo board, it read messages form the nucleo on one thread (like battery info) and sends messages to it from another (like speed command).
    - API that gathers data sent via UDP on the network (assync data, from cars and from semaphores)
    - API that communicates with the TrafficCommunication server. Gets location data from the localization device and sends traffic info to the server.
    - An asyncronous server-like process that communicates with the Demo project from the Computer. It acts as middle-ground between the car and the demo, gets movement commands from the PC or allows some parameters set. Allows the forwarding of data info from Brain project and displays them on the dashboard.