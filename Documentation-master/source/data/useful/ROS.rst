Robot Operating System
======================

ROS (Robot Operating System) is a robotic middleware (a collection of software frameworks for writing robot software). Although ROS is not an operating system , 
it provides services designed for a heterogeneous computer cluster such as hardware abstraction, low-level device control, implementation of commonly used 
functionality, message-passing between processes, and package management. Running sets of ROS-based processes(scripts) are represented in a graph architecture 
where processing takes place in nodes that may receive, post and multiplex sensor data, control, state, planning, actuator, and other messages via "topics", 
"services" and "actions". Despite the importance of reactivity and low latency in robot control, ROS itself is not a real-time OS (RTOS).
The main client libraries (C++, Python, and Lisp) are released under the terms of the BSD license as such as the other majority of available packages. 

ROS distributions
`````````````````
A ROS distribution is a versioned set of ROS packages. These are a kin to Linux distributions (e.g. Ubuntu). The purpose of the ROS distributions is to let developers work 
against a relatively stable codebase until they are ready to roll everything forward. The latest stable distribution that we encourage you to use is ROS Noetic, together 
with Ubuntu 20.04.

ROS installation
````````````````
You first have to install a supported operating system, either on your device or on a virtual machine. We suggest to not use a virtual machine since it may not have the same 
specifications as if installed directly on the HDD/SSD. 
For the Melodic installation, you can follow this link: http://wiki.ros.org/melodic/Installation/Ubuntu

In order to get started with the ROS functionalities, you can follow this guides:
http://wiki.ros.org/ROS/Tutorials