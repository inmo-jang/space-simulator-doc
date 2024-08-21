*******************************
Setting `config.yaml`
*******************************

**Prerequisite**: :doc:`Basic Usage <tutorial_basic_use>`

.. note::
    The following tutorials are interconnected. Therefore, it is recommended to follow them sequentially from the beginning.


.. contents:: Table of Contents







Changing the Decision-Making Plugin
=============================================================



Given a different *Decision-Making Plugin* that you want to test, you can easily switch it by updating the ``decision_making`` section in the configuration file. This allows you to change the decision-making functionality while keeping the rest of the scenario environment the same.

For example, based on the configuration file in :doc:`Basic Usage <tutorial_basic_use>` section, let us update the `decision_making` as follows:

.. code-block:: yaml

    decision_making:
      plugin: plugins.grape.grape.GRAPE
      GRAPE:
        cost_weight_factor: 1.0
        social_inhibition_factor: 100
        initialize_partition: Distance
        reinitialize_partition_on_completion: Distance

Then, the resultant file becomes the configuration file for :doc:`GRAPE <../plugins/grape>` section. 

Save this configuration file as ``config_grape.yaml``, and then execute the following command to run a simulation:

.. code-block:: shell

   python main.py --config=config_grape.yaml


Then, you will see a simulation similar to the following.

.. list-table::
   :widths: 50 50
   :header-rows: 0

   * - .. figure:: result/GRAPE_a10_t100_2024-08-20_17-50-35.gif
         :width: 93%
         :align: center

      

     - .. figure:: result/GRAPE_a10_t100_2024-08-20_17-50-35_timewise.png
         :width: 100%
         :align: center
            

------------------------            

Generating Dynamic Tasks
=============================================================        

.. note::   
   To avoid any confusion, it is important to clarify that in this tutorial, `dynamic tasks` refer to tasks that appear during the execution of the mission, rather than tasks that move spatially.

Currently, the settings related to task generation are configured as follows:

.. code-block:: yaml

    tasks:
      quantity: 100
      locations:
        x_min: 0
        x_max: 1400
        y_min: 0
        y_max: 1000
        non_overlap_radius: 0
      threshold_done_by_arrival: 10.0
      amounts:  
        min: 6.0
        max: 60.0      
      dynamic_task_generation:
        enabled: True
        interval_seconds: 2000
        max_generations: 3
        tasks_per_generation: 25


This configuration means that initially, 100 tasks are generated, and then every 2000 seconds, 25 additional tasks are created up to a maximum of 3 times.

If you wish to run the simulation without adding any additional tasks after the initial setup, modify the configuration as follows:        

.. code-block:: yaml

    tasks:
      quantity: 100    
      ....
      dynamic_task_generation:
        enabled: True
        ....

Then, run the simulation again. 

.. code-block:: shell

   python main.py --config=config_grape.yaml


Then, you will see a simulation similar to the following. In the graph on the right, you can observe that, with no dynamic tasks, the number of remaining tasks starts at 100 and decreases over time without increasing.

.. list-table::
   :widths: 50 50
   :header-rows: 0

   * - .. figure:: result/GRAPE_no_dynamic_task/GRAPE_a10_t100_2024-08-21_14-15-12.gif
         :width: 93%
         :align: center

      

     - .. figure:: result/GRAPE_no_dynamic_task/GRAPE_a10_t100_2024-08-21_14-15-12_timewise.png
         :width: 100%
         :align: center


