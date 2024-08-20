agents
==================


Parameters
------------------

:behavior_tree_xml:

  ============== =======
  Type           Default
  -------------- -------
  String         "default_bt.xml"
  ============== =======

  **Description**
    Specifies the behavior tree XML file that defines the behavior of agents.


:quantity:

  ============== =======
  Type           Default
  -------------- -------
  Integer        N/A
  ============== =======

  **Description**
    Specifies the number of agents to be created in the simulation.
    

:locations:
  **Description**
    Specifies the area where agents are uniformly randomly generated in the simulation. 

    - **x_min**: Minimum x-coordinate for agent placement. (Default: 0)
    - **x_max**: Maximum x-coordinate for agent placement. (Default: 1400)
    - **y_min**: Minimum y-coordinate for agent placement. (Default: 0)
    - **y_max**: Maximum y-coordinate for agent placement. (Default: 1000)
    - **non_overlap_radius**: Minimum distance between agents to avoid initial overlap. (Default: 0) **Note**: A non-zero value may increase simulation initialization time. For optimal performance, use the default value.

:max_speed:

  ============== =======
  Type           Default
  -------------- -------
  Float          0.25
  ============== =======

  **Description**
    Maximum speed an agent can achieve. `0.25` means that the agent can move 0.25 pixels per simulation-time second (not real-time second). 
    

:max_accel:

  ============== =======
  Type           Default
  -------------- -------
  Float          0.05
  ============== =======

  **Description**
    Maximum acceleration an agent can achieve. `0.05` means the agent can increase `0.05` pixels per simulation-time second squared. 

:max_angular_speed:

  ============== =======
  Type           Default
  -------------- -------
  Float          0.25
  ============== =======

  **Description**
    Maximum angular speed (rotation speed) of an agent. `0.25` means that the agent can rotate at `0.25` radian per simulation-time second (not real-time second). 


:target_approaching_radius:

  ============== =======
  Type           Default
  -------------- -------
  Float          50.0
  ============== =======

  **Description**
    Distance within which an agent starts slowing down as it approaches its target.

:work_rate:

  ============== =======
  Type           Default
  -------------- -------
  Float          1.0
  ============== =======

  **Description**
    The rate at which an agent completes its assigned tasks (in simulation time). 

:communication_radius:

  ============== =======
  Type           Default
  -------------- -------
  Float          500.0
  ============== =======

  **Description**
    The maximum distance within which each agent can communicate with other agents.

:situation_awareness_radius:

  ============== =======
  Type           Default
  -------------- -------
  Float          500.0
  ============== =======

  **Description**
    The maximum distance within which each agent is aware of tasks.

:random_exploration_duration:

  ============== =======
  Type           Default
  -------------- -------
  Float          1000.0
  ============== =======

  **Description**
    Specifies the duration (in simulation time) during which agents continuously travel towards a randomly chosen position. This behavior occurs when agents are not assigned any tasks. The agent will maintain this movement towards the random position for the specified duration before being assigned a task by the decision-making plugin.



Example
------------------

.. code-block:: yaml

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
