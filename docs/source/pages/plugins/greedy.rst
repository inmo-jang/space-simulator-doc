First-Claimed Greedy
====================

This plugin implements the **First-Claimed Greedy** algorithm, a straightforward approach where each agent selects the nearest task based on local task information. The agent also considers messages from neighboring agents to avoid task conflicts.


In this algorithm, each agent follows these steps:

1. **Choose the nearest task**: The agent selects the task closest to its current position.
2. **Consider neighboring agents**: The agent checks the status of tasks claimed by neighboring agents.
3. **Handle conflicts**: If the chosen task has already been claimed by another agent, the agent abandons the task and will attempt to select a new one in the next iteration.

The **First-Claimed Greedy** algorithm ensures that an agent’s initial claim on a task is upheld, and conflicts are resolved in subsequent steps. This approach minimizes task reassignment and optimizes task allocation based on proximity and real-time updates from neighboring agents.


An example of the parameters look like as follows:

.. code-block:: yaml

    decision_making: 
      plugin: plugins.greedy.greedy.FirstClaimGreedy
      FirstClaimGreedy:  
        mode: MinDist  # Options: Random; MinDist; MaxUtil
        weight_factor_cost: 10000.0 # Only used for `MaxUtil` mode

Parameters
----------------------

:mode:
  
  ============== =======
  Type           Default
  -------------- -------
  String         MinDist
  ============== =======
  
  **Description:**  
    Determines the logic by which an agent selects a task from the available local tasks. The options are:
    
    - ``Random``: Selects a task randomly.
    - ``MinDist``: Chooses the task that is closest to the agent.
    - ``MaxUtil``: Selects the task with the highest utility. The utility is currently calculated as:
      
      .. code-block:: python
      
          utility = task.amount - weight_factor_cost * (self.agent.position - task.position).length()
  
:weight_factor_cost:

  ============== =======
  Type           Default
  -------------- -------
  Float          10000.0
  ============== =======
  
  **Description:**  
    This parameter is used in the ``MaxUtil`` mode to influence the weighting factor for the cost component in the utility calculation. It determines the magnitude of the impact of distance on task utility.


Example `config.yaml`
------------------------

.. figure:: result/FirstClaimGreedy_a10_t100_2024-08-20_19-08-36.gif
   :width: 600
   :height: 450
   :alt: GIF of First-Claimed Greedy Sample Result

This was executed with the following configuration:

.. code-block:: yaml

    decision_making: 
      plugin: plugins.greedy.greedy.FirstClaimGreedy
      FirstClaimGreedy:  
        mode: MinDist  
        weight_factor_cost: 10000.0 # Only used for `MaxUtil` mode

    agents:
      behavior_tree_xml: default_bt.xml 
      quantity: 10
      locations:
        x_min: 0
        x_max: 1400
        y_min: 0
        y_max: 1000
        non_overlap_radius: 0 
      max_speed: 0.25  
      max_accel: 0.05
      max_angular_speed: 0.25
      target_approaching_radius: 50
      work_rate: 1  
      communication_radius: 500 
      situation_awareness_radius: 500 
      random_exploration_duration: 1000.0 

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

    simulation:
      sampling_freq: 1.0 
      speed_up_factor: 0 
      max_simulation_time: 0
      agent_track_size: 400  
      screen_width: 1400 
      screen_height: 1000 
      gif_recording_fps: 0.05  
      task_visualisation_factor: 3  
      profiling_mode: False
      rendering_mode: Screen  
      rendering_options: 
        agent_tail: True
        agent_communication_topology: True
        agent_situation_awareness_circle: False
        agent_id: True
        agent_work_done: True
        agent_assigned_task_id: True
        agent_path_to_assigned_tasks: True
        task_id: False
      saving_options:
        output_folder: output
        with_date_subfolder: True
        save_gif: False
        save_timewise_result_csv: True    
        save_agentwise_result_csv: True
        save_config_yaml: True
