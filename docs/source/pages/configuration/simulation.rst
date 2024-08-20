simulation
=============

Parameters
------------------

:sampling_freq:

  ============== =======
  Type           Default
  -------------- -------
  Float          1.0
  ============== =======

  **Description**
    The sampling frequency (in Hz) at which the simulation loop is executed. This frequency determines how often the behavior trees of all agents are processed.


:speed_up_factor:

  ============== =======
  Type           Default
  -------------- -------
  Integer        0
  ============== =======

  
  **Description**
    A factor that adjusts the speed of the simulation. A value of `0` represents the fastest possible simulation speed. A value of `1` corresponds to real-time simulation, while values greater than `1` accelerate the simulation further.



:max_simulation_time:

  ============== =======
  Type           Default
  -------------- -------
  Integer        0
  ============== =======

  **Description**
    The maximum duration (in simulation-time seconds) for the simulation. A value of `0` means no time limit. 


:agent_track_size:

  ============== =======
  Type           Default
  -------------- -------
  Integer        400
  ============== =======

  **Description**
    The size of the trail (in pixels) shown behind each agent to visualize its travelled path.


:screen_width:

  ============== =======
  Type           Default
  -------------- -------
  Integer        1400
  ============== =======

  **Description**
    The width of the simulation window in pixels.


:screen_height:

  ============== =======
  Type           Default
  -------------- -------
  Integer        1000
  ============== =======

  **Description**
    The height of the simulation window in pixels.


:gif_recording_fps:

  ============== =======
  Type           Default
  -------------- -------
  Float          0.05
  ============== =======

  **Description**
    The frame rate (in frames per simulation-time second) used for recording the simulation as a GIF. A value of `10` means that 10 frames isare saved every simulation-time second. Conversely, a value of `0.05` means that a frame is saved every 20 simulation-time seconds.

    This setting is effective only if GIF recording is enabled. To enable GIF recording, set ``save_gif`` to ``True`` in the configuration file or press the ``r`` key during the simulation.



:task_visualisation_factor:

  ============== =======
  Type           Default
  -------------- -------
  Integer        3
  ============== =======

  **Description**
    The factor that determines the size of task visualizations relative to their workload. A value of `10` means that 10 units of workload are represented by 1 pixel. A higher value reduces the size of the visualized tasks, making them appear smaller on the screen.



:profiling_mode:

  ============== =======
  Type           Default
  -------------- -------
  Boolean        False
  ============== =======

  **Description**
    Indicates whether profiling mode is active. When enabled, the simulation runs with ``cProfile``, which collects performance metrics such as the computational cost of each function. This mode provides detailed insights into the performance characteristics of the simulation.



:rendering_mode:

  ============== =======
  Type           Default
  -------------- -------
  String         "Screen"
  ============== =======

  **Description**
    Specifies the rendering mode used to display the simulation. Options include:

    - **Screen**: Renders the simulation visually on the screen.
    - **Terminal**: Provides descriptive rendering in the terminal.
    - **None**: Disables visual rendering, only generating result files.


:rendering_options:

  **Description**
    Specifies additional rendering options that apply only when the ``rendering_mode`` is set to ``Screen``. 

    - **agent_tail**: Whether to display the trail behind agents. (Default: True)
    - **agent_communication_topology**: Whether to visualize the communication topology of agents. (Default: True)
    - **agent_situation_awareness_circle**: Whether to show the situation awareness circle around agents. (Default: False)
    - **agent_id**: Whether to display agent IDs. (Default: True)
    - **agent_work_done**: Whether to show the amount of work done by each agent. (Default: True)
    - **agent_assigned_task_id**: Whether to display the ID of tasks assigned to agents. (Default: True)
    - **agent_path_to_assigned_tasks**: Whether to visualize the path from agents to their assigned tasks. (Default: True)
    - **task_id**: Whether to show task IDs. (Default: False)


:saving_options:

  **Description**
    Specifies options for saving simulation data.

    - **output_folder**: Directory where simulation results are saved. (Default: ``output``)
    - **with_date_subfolder**: Whether to create a date-based subfolder within the output directory. (Default: True)
    - **save_gif**: Whether to save the simulation as a GIF. (Default: False)
    - **save_timewise_result_csv**: Whether to save time-wise results to a CSV file. (Default: True)
    - **save_agentwise_result_csv**: Whether to save agent-wise results to a CSV file. (Default: True)
    - **save_config_yaml**: Whether to save the configuration YAML file used for the simulation. (Default: True)


**Example**
------------------

.. code-block:: yaml

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
