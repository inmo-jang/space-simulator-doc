.. _tutorial_custom_bt:

Adding a Custom Behavior Tree
*******************************

**Prerequisite**: :ref:`tutorial_basic_use`


.. contents:: Table of Contents



--------------------

Opening the Default Behavior Tree with Groot2
=============================================

Let's open the currently defined default behavior tree using Groot2. First, download Groot2. Groot2 can be downloaded from https://www.behaviortree.dev/groot/ and is a GUI tool created for ``BehaviorTree.CPP``. Run Groot2 and open ``/bt_xml/default_bt.xml``. You will then be able to visualize the default behavior tree as shown below.


- .. figure:: custom_bt/groot_02.png
    :width: 70%
    :align: center

    **Figure 1:** Groot2 with ``default_bt.xml``


.. note::

   Groot2 was originally created for ``BehaviorTree.CPP``, but in the SPADE simulator, only the visualization functionality of the Behavior Tree is used. Therefore, the other features do not work.


In the default behavior tree (i.e., ``/bt_xml/default_bt.xml``), agents start with the ``LocalSensingNode`` to detect nearby tasks and messages. They then proceed to the ``DecisionMakingNode`` for task assignments, followed by the ``TaskExecutionNode`` to perform the task. If no tasks are detected, the agent executes the ``ExplorationNode`` to move to a random position and search for tasks.
You can observe this behavior by following the test in :ref:`tutorial_basic_use`.

In this tutorial, we will attempt to modify this behavior tree.
