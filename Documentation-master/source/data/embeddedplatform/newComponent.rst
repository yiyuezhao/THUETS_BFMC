New component
=============

When you want to implement some new feature, it's recommended to keep clean the project structure. With this in mind, you will notice that the "include"
and the "source" directory are following the same structure, ".hpp" files being under the the "include" and ".cpp" files under source. 

To facilitate the addition of new components to the project, utilize the newComponent.py script. This script automates the process of creating the necessary files and directories for a new component, adhering to the existing structure of the project.

**Utilizing the newComponent.py Script**

Here is how you can use the script:

1. Navigate to the directory where the newComponent.py script is located (should be inside the project directory).

.. code-block::

   Embedded_Platform\newComponent\newComponent.py

2. Run the script in a terminal or an IDE.
3. When prompted, input the category of the component (existing options are "brain," "driver," "periodics," or "utils").
4. Next, input the name of the new component.

Notes
------

The script for creating a new component (newComponent.py) and for flashing the micro-controller weren't projected to linux usage, so we cannot guarantee the 
correct working. 