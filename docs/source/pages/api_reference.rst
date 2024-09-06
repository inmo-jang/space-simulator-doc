.. _api_reference:

API Reference
***********************

.. contents:: Table of Contents


-----------------------------------------

Agent (``agent.py``)
===========================================

The ``Agent`` class, defined in ``modules/agent.py``, encapsulates the core attributes and methods relevant to each agent within the SPACE simulator.

Attributes
------------------------

- **Static:** Following attributes are static during a mission.

  - ``agent_id`` (int): The unique identification number of the agent.
  - ``max_speed`` (float): The maximum speed the agent can achieve.
  - ``max_accel`` (float): The maximum acceleration the agent can achieve.
  - ``max_angular_speed`` (float): The maximum angular speed (rotation) of the agent.
  - ``work_rate`` (float): The rate at which the agent can work on tasks per simulation time.
  - ``communication_radius`` (float): The radius within which the agent can communicate with other agents.
  - ``situation_awareness_radius`` (float): The radius within which the agent is aware of tasks.

- **Agent Movement:**

  - ``position`` (pygame.Vector2): The current position of the agent as a `pygame.Vector2` object.
  - ``velocity`` (pygame.Vector2): The current velocity of the agent as a `pygame.Vector2` object.
  - ``acceleration`` (pygame.Vector2): The current acceleration of the agent as a `pygame.Vector2` object.
  - ``rotation`` (float): The current rotation angle of the agent, used for direction.
  - ``color`` (tuple of int): The color of the agent, used for visual representation (RGB). This color is changed to black if there is no assigned task. if the agent is assigned to a task, then the agent is colored to the same color of the task. 

- **Behavior Tree:**

  - ``blackboard`` (dict): A dictionary storing the agent's internal state and information relevant to the behavior tree.

- **Global Information:**

  - ``tasks_info`` (list of Task): Global information about tasks in the environment. 
  - ``agents_info`` (list of Agent): Global information about other agents in the environment.

- **Local Information:**

  - ``agents_nearby`` (list of Agent): List of nearby agents within the communication radius.
  - ``message_to_share`` (dict): Dictionary of messages that the agent is sharing with neighboring agents.
  - ``messages_received`` (list of dict): List of messages received from neighboring agents.

- **Decision-Making Results:**

  - ``assigned_task_id`` (int or None): The ID of the task currently assigned to the agent, or `None` if no task is assigned.
  - ``planned_tasks`` (list of Task): List of tasks that the agent has planned or is considering.

- **Mission Statistics:**

  - ``distance_moved`` (float): The total distance traveled by the agent.
  - ``task_amount_done`` (float): The total amount of work completed by the agent.


Key Functions
----------------------------

- **Behavior Tree:**

  - ``create_behavior_tree()``: Loads the behavior tree XML file and constructs the behavior tree for the agent.
  - ``run_tree()``: Executes the agent's behavior tree during each game loop iteration.

- **Local Information:**

  - ``local_message_receive()``: Receives messages from neighboring agents and updates the ``messages_received`` list. This method is typically called to process incoming messages during each game loop iteration at ``LocalSensingNode``. 
  - ``reset_messages_received()``: Clears the ``messages_received`` list.

  - ``get_agents_nearby(radius=None)``: Retrieves a list of nearby agents within the communication radius. If `radius` is provided, it overrides the default communication radius.
  - ``get_tasks_nearby(radius=None, with_completed_task=True)``: Retrieves a list of nearby tasks within the situational awareness radius. If `radius` is provided, it overrides the default radius. If `with_completed_task` is `False`, only incomplete tasks are retrieved.


- **Movement:**

  - ``update_task_amount_done(amount: float)``: Updates the ``task_amount_done`` attribute by adding the specified `amount` of work completed. This method is used to track the total amount of work done by the agent and helps in monitoring the agent's progress towards task completion.

  - ``follow(target: pygame.Vector2)``: Moves the agent towards the specified target position.
  - ``applyForce(force: pygame.Vector2)``: Applies a force to the agent's acceleration.
  - ``update()``: Updates the agent's position, velocity, and rotation based on the current acceleration.
  - ``reset_movement()``: Resets the agent's velocity and acceleration.

- **Rendering:**  

  - ``draw(screen: pygame.Surface)``: Draws the agent on the screen.
  - ``draw_tail(screen: pygame.Surface)``: Draws the agent's movement trail on the screen.
  - ``draw_communication_topology(screen: pygame.Surface, agents: list of Agent)``: Draws lines connecting the agent to its neighboring agents.
  - ``draw_agent_id(screen: pygame.Surface)``: Draws the agent's ID on the screen.
  - ``draw_assigned_task_id(screen: pygame.Surface)``: Draws the IDs of assigned tasks on the screen.
  - ``draw_work_done(screen: pygame.Surface)``: Draws the total distance moved and work done by the agent on the screen.
  - ``draw_situation_awareness_circle(screen: pygame.Surface)``: Draws a circle representing the agent's situational awareness radius.
  - ``draw_path_to_assigned_tasks(screen: pygame.Surface)``: Draws paths to the agent's assigned tasks.
  - ``set_planned_tasks(planned_tasks: list of Task)``: Sets ``planned_tasks``. This is for mostly visualization purpose. 
  - ``update_color()``: Updates the agent's color based on the assigned task.

-----------------------------------------

Task (``task.py``)
===========================================

The ``Task`` class, defined in ``task.py``, represents individual task instances within the simulation.



Attributes
-------------------

- ``task_id`` (int): The unique identification number of the task.
- ``position`` (pygame.Vector2): The current position of the task as a `pygame.Vector2` object.
- ``amount`` (float): The amount of work required to complete the task.
- ``completed`` (bool): A boolean indicating whether the task has been completed.
- ``color`` (tuple of int): The color of the task, used for visual representation (RGB).
- ``radius`` (float): The visual radius of the task, which scales with the amount of work required.



Key Functions
------------------------

- **Task Management:**

  - ``set_done()``: Marks the task as completed.
  - ``reduce_amount(work_rate: float)``: Reduces the task amount based on the provided ``work_rate``. If the task amount reaches 0 or below, the task is marked as completed.

- **Rendering:**

  - ``draw(screen: pygame.Surface)``: Draws the task on the screen based on its amount and completion status.
  - ``draw_task_id(screen: pygame.Surface)``: Draws the task ID and remaining amount on the screen.
