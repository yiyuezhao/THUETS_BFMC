Simulated servers
=================

To start the simulated servers you will have to open two terminals(one for each one of them).


In the first terminal run the following command. It will simulate the communication the trafficCommunicationServer and the getting of positions from it.


.. code-block:: bash

    cd Computer/servers/trafficCommunicationServer
    python3 TrafficCommunication.py


In the second terminal run the following command. It will simulate the streaming data from the semaphore.

.. code-block:: bash

    cd Computer/servers/SemaphoreStreamSIM
    python3 udpStreamSIM.py
