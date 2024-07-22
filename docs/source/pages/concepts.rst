


**********************
Simulator Architecture
**********************


TBD 


-----------------------------------------


**********************
Major Features
**********************





High-level Decision Making
--------------------------

The SPADE simulator is designed to support research in high-level decision-making for multi-robot systems and swarm robotics, with a particular focus on multi-robot task allocation (MRTA) problems.
This simulator is optimized for scalability, accommodating hundreds of agents to facilitate swarm-level testing. It is designed to be lightweight, with minimal dependencies beyond Python. 
This design choice ensures cross-platform compatibility and ease of setup. 

.. note::
    Although integration with ROS2 was considered initially, it was not implemented to maintain simplicity and reduce dependencies.

While it would be ideal to consider the dynamics of each agent and collision-free path planning, including collision avoidance between agents, this simulator focuses on the evaluation and comparative analysis of high-level decision-making algorithms. Therefore, agents are modeled with point mass dynamics.

Agents are assumed to perform obstacle avoidance and inter-agent collision avoidance during task execution, but in the simulator, agents move in straight lines to their assigned tasks. This assumption allows the simulator to accommodate a large number of agents for high-level decision-making evaluation.


Local Information
------------------
**Evaluation of Decentralized Decision-Making Algorithms**: The simulator emphasizes the evaluation of decentralized decision-making algorithms. Agents can communicate with neighboring agents within their communication radius and receive updates on tasks within their situational awareness radius. For instance, information about newly discovered or completed tasks is updated only within the agent's situational awareness radius.

Dynamic Task Generation Scenario
--------------------------------
**Dynamic Task Generation**: Traditional testing often involves generating random tasks and agent capabilities, followed by task assignment using decision-making algorithms. This simulator extends the evaluation to scenarios where tasks are continuously generated during the mission.

Behavior-Tree
-----------------
**Behavior Tree Framework**: The basic behavior of agents is defined using behavior trees. One of the action nodes within the behavior tree is the decision-making node, which executes the decision-making algorithm. The use of behavior trees allows for easy modification of agent behavior by implementing new action nodes and integrating them into the tree. The behavior trees can be visualized and edited using Groot2 (https://www.behaviortree.dev/groot/), a GUI tool originally developed for BT.CPP.

Inter-Algorithms Comparative Analysis
-------------------------------------
**Comparative Analysis of MRTA Algorithms**: Comparing different MRTA algorithms under the same scenario is challenging due to the unique nature of each algorithm. Pseudo-code alone is insufficient; interfacing and wrapping tasks are required to adapt the algorithms to the simulator. By using behavior trees as the foundation for agent behavior, the simulator allows for flexible evaluation of diverse algorithms in a common scenario. For example, the GRAPE algorithm can be applied to SR-MT MRTA problems. To facilitate comparative analysis, the simulator supports Monte Carlo tests with statistical analysis configurable via YAML settings.

Configurability
---------------
**Ease of Configuration**: The simulator allows for easy replacement of decision-making plugins and adjustment of scenario generation settings by simply modifying the `config.yaml` file. There is no need to alter the simulator's source code. New decision-making algorithms can be implemented as plugins and integrated by updating the configuration file, enabling straightforward testing of new algorithms.








