**********************
Getting Started
**********************




The SPADE simulator is designed specifically for swarm simulations, with an emphasis on being as lightweight as possible. Consequently, it has been developed to have no dependencies beyond Python itself. You only need to install a few Python packages to use the simulator. This approach also ensures that the simulator is OS-independent. 


Installation
=============

Follow these steps to install the SPADE simulator.

Clone the repository:

.. code-block:: bash

   git clone https://github.com/inmo-jang/spade-simulator.git
   cd spade-simulator

Install the required dependencies:

.. code-block:: bash

   pip install -r requirements.txt


Run the Simulator
=================

You can run the simulator by executing the following command in the command line. By default, the simulator uses ``config.yaml`` as the default configuration file.

.. code-block:: bash

   python main.py

If you want to use a specific configuration (e.g., ``my_config.yaml``), you can run:

.. code-block:: bash

   python main.py --config=path_to/my_config.yaml


For details on configuration settings, please refer to the :doc:`Configuration Guide <configuration>`.