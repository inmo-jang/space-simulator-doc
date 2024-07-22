.. spade-simulator documentation master file, created by
   sphinx-quickstart on Sun Jul 21 23:26:20 2024.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

SPADE Simulator Documentation
=============================


Welcome to the official documentation for **SPADE** (Swarm Planning And Decision Evaluation) Simulator. 
This simulator is designed to facilitate research and development in swarm robotics and decentralized decision-making. Below are the key features of the SPADE simulator:


Key Features
------------


- **Swarm Robotics Focus**: Optimized for swarm robotics research, supporting large-scale simulations with a lightweight design.
- **Behavior Trees**: Uses behavior trees to define and manage agent behaviors, allowing for flexible and structured decision-making.   
- **Local Communication and Awareness**: Agents communicate locally within specified radii and maintain situational awareness based on their situational awareness ranges.
- **Flexible Configuration**: Easily configurable via YAML files, enabling customization without modifying the simulator’s source code.
- **Custom Plugins**: Integrates custom decision-making algorithms as plugins, allowing for tailored testing and experimentation.
- **Groot2 Integration**: Compatible with Groot2 for visualizing and editing the agents' behavior trees, enhancing ease of use and analysis.
- **Dynamic Task Generation**: Supports the creation of tasks dynamically during the simulation, adapting to evolving scenarios.
- **Algorithm Comparison**: Facilitates the comparison of different decision-making algorithms within a consistent simulation environment and supports Monte Carlo tests for statistical analysis and rigorous comparative evaluation.





For detailed installation instructions, please refer to the :doc:`Installation Guide <pages/quickstart>`.



.. list-table::
   :widths: 50 50
   :header-rows: 0

   * - .. figure:: assets/GRAPE_20_agents_200_tasks.gif
         :width: 100%
         :align: center
         
         **Figure 1:** GRAPE with 20 agents and 200 tasks.
     - .. figure:: assets/GRAPE_500_agents_10_tasks.gif
         :width: 100%
         :align: center
         
         **Figure 2:** GRAPE with 500 agents and 10 tasks.




.. toctree::
   :maxdepth: 2
   :caption: Quick Start
   :hidden:

   pages/quickstart

.. toctree::
   :maxdepth: 2
   :caption: Simulation Concepts
   :hidden:

   pages/concepts


.. toctree::
   :maxdepth: 2
   :caption:  Tutorials
   :hidden:
   
   pages/tutorial_config
   pages/tutorial_plugin   
   pages/tutorial_bt
   pages/tutorial_monte_carlo


.. toctree::
   :maxdepth: 2
   :caption:  User Guide
   :hidden:

   pages/configuration   
   pages/plugin
   pages/api_reference
   
   
      