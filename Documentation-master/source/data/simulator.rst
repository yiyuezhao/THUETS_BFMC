Simulator
=========

Installing the simulator on the PC
----------------------------------

The Ubuntu version is 20.04, while the ROS version is Noetic. Though, any Ubuntu and ROS 1 newer version should work. 

Other two branches are created in the same repo, each made available by a team whose name is in the branch itself.

Now clone the Simulator project inside the Documents folder of your PC. Then follow the next steps in order to build,
source and run the simulator (change the {YOUR_USER} text with your actual username. 

.. code-block:: bash
    
    catkin_make --pkg utils
    catkin_make
    echo 'export GAZEBO_MODEL_PATH="/home/{YOUR_USER}/Documents/Simulator/src/models_pkg:$GAZEBO_MODEL_PATH"' > devel/setup.bash
    export 'ROS_PACKAGE_PATH="/home/{YOUR_USER}/Documents/Simulator/src:$ROS_PACKAGE_PATH"'> devel/setup.bash
    source devel/setup.bash
    roslaunch sim_pkg map_with_all_objects.launch

Now open two other terminals and do the following

.. code-block:: bash

    source devel/setup.bash
    rosrun example camera.py

.. code-block:: bash

    source devel/setup.bash
    rosrun example control.py


Additional notes
----------------

**Camera**

You can change the resolution and the position of the camera, just have this files in mind:

`src/models_pkg/camera/model.sdf`

You will find the `<width>` and `<height>` tags. Modifying them will allow you to change the camera resolution. You don't need to recompile the workspace after this change.

`src/models_pkg/rcCar_assembly/model.sdf`
you will find the inclusion of `<uri>model://camera</uri>`. Inside that same `<include>` tag, there is also a `<pose>` tag, which you will need to modify `according to the 
SDF format specification <http://sdformat.org/spec?ver=1.6&elem=model#include_pose>`_ in order to change the camera's position. You don't need to recompile the workspace after 
this change.
All constants of double data type, with angles in radians and "." (dot) as decimal separator, as in this example:
'<pose> X Y Z ROLL PITCH YAW </pose>'

**Working with gazebo:**
    - If you want to restart the simulation, instead of restarting gazebo, you can only restart the simulation with the help of the ROS services, such as: 'rosservice call /gazebo/reset_simulatio'
    - Deactivate GUI from the launch in order to save some computational power.
    - Play with rqt tool in order to check the images and other topic messages, frequency, etc.
    - You can change the resolution of the map from `src/models_pkg/track/materials/scripts/bfmc_track.material`. The available maps are under the textures directory. Bigger the resolution, bigger the requirements of the simulation.
    - Inside the `src/sim_pkg/launch/sublaunchers` directory, there is a launch file for each type of elements on the map or groups of elements. You can also spawn some of them separately while the simulator is running, based on the requirements at the moment. 
    - You can also configure your own launching files, you can create a launch file that includes multiple launch files. See the `map_with_all_objects.launch` file inside the `src/sim_pkg/launch` as an example.


ROS vehicle and simulator integration
-------------------------------------

Both the car and the PC running the simulation have to be on the same network and the ssh communication has to be enabled on the RPi. 
In order for the nodes to be able to communicate between them, some environmental variables have to be set. A set of environmental 
variables must be set for ROS to be able to communicate between the devices.This setup will make the nodes on your car interact with 
the roscore from the PC, and you will be able to see the entire setup of the network (The roscore can be swapped to run on the physical car as well).

**On the RPI:**

.. code-block:: bash

    export ROS_IP=`hostname -I`
    export ROS_HOSTNAME=`hostname -I`
    export ROS_MASTER_URI="http://PC_IP:11311"

, where PC_IP is the IP of the PC on the LAN.

**On the PC:**

.. code-block:: bash

    export ROS_IP=`hostname -I`
    export ROS_HOSTNAME=`hostname -I`
    export ROS_MASTER_URI="http://$ROS_IP:11311"


Then, just execute the normal launches:

**On the RPI:**

.. code-block:: bash

    cd Brain_ROS
    source devel/setup.bash
    roslaunch sim_pkg start_car_virtual.launch

**On the PC:**

.. code-block:: bash

    cd Simulator
    source devel/setup.bash
    roslaunch sim_pkg map_with_car.launch

Now the simulator will publish some info on the topics and you can subscribe to them from your car (automobile/image_raw, 
automobile/localization, automobile/IMU, automobile/feedback, automobile/semaphores/_). The simulator will also subscribe to 
some info on the topics and you can publish on them from your car (automobile/command)
