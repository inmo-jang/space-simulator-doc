.. _tutorial_changing_plugin:


Changing the Decision-Making Plugin
========================================

**Prerequisite**: :ref:`tutorial_basic_use`



Given a different *Decision-Making Plugin* that you want to test, you can easily switch it by updating the ``decision_making`` section in the configuration file. This allows you to change the decision-making functionality while keeping the rest of the scenario environment the same.

For example, based on the configuration file in :ref:`tutorial_basic_use` section, let us update the ``decision_making`` as follows:

.. code-block:: yaml

    decision_making:
      plugin: plugins.grape.grape.GRAPE
      GRAPE:
        cost_weight_factor: 1.0
        social_inhibition_factor: 100
        initialize_partition: Distance
        reinitialize_partition_on_completion: Distance


Save this configuration file as ``config_grape.yaml``, and then execute the following command to run a simulation:

.. code-block:: shell

   python main.py --config=config_grape.yaml


Then, you will see a simulation similar to the following.

.. list-table::
   :widths: 50 50
   :header-rows: 0

   * - .. figure:: result/GRAPE/GRAPE_a10_t100_2024-08-20_17-50-35.gif
         :width: 93%
         :align: center

      

     - .. figure:: result/GRAPE/GRAPE_a10_t100_2024-08-20_17-50-35_timewise.png
         :width: 100%
         :align: center



See the configuration file used for the above simulation: :download:`config_grape.yaml <result/GRAPE/GRAPE_a10_t100_2024-08-20_17-50-35.yaml>`.    