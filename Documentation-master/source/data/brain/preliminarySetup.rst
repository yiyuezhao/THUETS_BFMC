Preliminary Setup
=================

Download Raspberry Pi Imager
-----------------------------
You can download the Raspberry Pi Imager from the official website: https://www.raspberrypi.com/software

.. image:: ../../images/brain/raspberry.png
    :align: center
    :width: 80%

Choose the Raspberry Pi OS
---------------------------
When configuring the Raspberry Pi Imager, select "Raspberry Pi OS Lite" as your operating system (OS) of choice.

.. image:: ../../images/brain/raspberryOptions.png
    :align: center
    :width: 80%

Set Up Your Raspberry Pi
-------------------------
- Configure your desired username and password.
- Set up your Wi-Fi network settings.
- Enable SSH connection for remote access.

.. image:: ../../images/brain/raspberrySettings.png
    :align: center
    :width: 80%

Write the OS Image
-------------------
Use Raspberry Pi Imager to write the selected OS image to your SD card.

Insert SD Card and Power Up Raspberry Pi
-----------------------------------------
Place the SD card into your Raspberry Pi and power it up.

Find the IP Address of Your Raspberry Pi
-----------------------------------------
Locate the IP address of your Raspberry Pi on your local network.

.. image:: ../../images/computer/raspberry_address.png
    :align: center
    :width: 80%

Connect to the Raspberry Pi via ssh
------------------------------------
Use SSH to establish a connection to your Raspberry Pi:

.. code-block:: bash

   ssh <username>@<Raspberry_Pi_IP_Address>
    

Clone the Brain Repository
---------------------------
Clone the Brain repository from GitHub to your desired location (e.g., under "Documents"):

.. code-block:: bash

   git clone https://github.com/ECC-BFMC/Brain
   


Update and Install Necessary Software
--------------------------------------
Run the following commands to update and upgrade your Raspberry Pi's software and install required packages:

.. code-block:: bash
   
    cd Brain
    sudo apt update
    sudo apt upgrade
    pip3 install -r requirements.txt
    xargs sudo apt install -y < "requirement.txt" 
    cd src/dashboard/frontend/ 
    curl -fsSL https://fnm.vercel.app/install | bash 
    source ~/.bashrc 
    fnm install --lts 
    npm install -g @angular/cli@17 
    npm install


Start the code
--------------

We just need to power up the main

.. code-block:: bash
   
    cd ../../../
    python3 main.py

Automatic start
----------------

If you want your code to run automatically at startup, we need to set the file as exec 
rights from anywhere, create a new service that starts the app and then make the service go at startup

.. code-block:: bash
   
    chmod +x main.py
    sudo nano /etc/systemd/system/BFMCcar.service

Now add this to the file:

.. code-block:: bash
   
    [Unit]
    Description=My Python Script Service
    After=multi-user.target

    [Service]
    Type=idle
    User=pi
    ExecStart=/usr/bin/python3 /home/pi/Brain/main.py

    [Install]
    WantedBy=multi-user.target

Let's make it run at startup:

.. code-block:: bash
   
    sudo systemctl daemon-reload
    sudo systemctl enable BFMCcar.service
    sudo systemctl start BFMCcar.service
    sudo systemctl status my_python_script.service

Now the code will start running in this session, and from now on it will go automatically at startup.

For debugging and logging:

.. code-block:: bash
   
    sudo systemctl status my_python_script.service
    journalctl -u my_python_script.service


Enjoy Your Raspberry Pi Brain Setup
------------------------------------
Your Raspberry Pi is now set up with the Brain repository, and all the necessary software is installed. Enjoy exploring and experimenting with your Raspberry Pi Brain project!
