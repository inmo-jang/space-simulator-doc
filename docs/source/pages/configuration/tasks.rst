tasks
=========

Parameters
------------------


:quantity:

  ============== =======
  Type           Default
  -------------- -------
  Integer        100
  ============== =======

  **Description**
    Specifies the total number of tasks to be generated in the simulation.


:locations:

  **Description**
    Specifies the area where tasks are uniformly randomly generated in the simulation.

    - **x_min**: Minimum x-coordinate for task placement. (Default: 0)
    - **x_max**: Maximum x-coordinate for task placement. (Default: 1400)
    - **y_min**: Minimum y-coordinate for task placement. (Default: 0)
    - **y_max**: Maximum y-coordinate for task placement. (Default: 1000)
    - **non_overlap_radius**: Minimum distance between tasks to prevent overlap at initialization. (Default: 0) **Note**: Setting this value to a non-zero value may slow down simulation initialization. It is recommended to use the default value for optimal performance.


:threshold_done_by_arrival:

  ============== =======
  Type           Default
  -------------- -------
  Float          10.0
  ============== =======

  **Description**
    The distance within which a task is considered being executed once an agent reaches it.


:amounts:

  **Description**
    Specifies the range of workload amounts for tasks. Workload amounts are uniformly randomly assigned to each task within the following range.

    - **min**: Minimum workload amount. (Default: 6.0)
    - **max**: Maximum workload amount. (Default: 60.0)


:dynamic_task_generation:

  **Description**
    Controls the dynamic generation of tasks during the simulation.

    - **enabled**: Whether dynamic task generation is enabled. (Default: True)
    - **interval_seconds**: Time interval (in seconds of simulation time) between each task generation. (Default: 2000)
    - **max_generations**: Maximum number of dynamic task generations allowed. (Default: 3)
    - **tasks_per_generation**: Number of tasks generated per dynamic generation. (Default: 25)


Example
------------------

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
