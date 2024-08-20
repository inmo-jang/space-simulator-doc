decision_making 
====================


Parameters
------------------

:plugin:

  ============== =======
  Type           Default
  -------------- -------
  String         N/A
  ============== =======

  **Description**
    Specifies the Python module path and class name that define the decision-making logic for agents.


    The following plugins are currently implemented:

    - ``plugins.cbba.CBBA``
    - ``plugins.grape.GRAPE``
    - ``plugins.greedy.FirstClaimGreedy``    

    Each plugin may have its own specific parameters. For detailed information, please visit the :doc:`Decision-Making Plugins <../plugin_index>` page.




Example
------------------

.. code-block:: yaml

    decision_making: 
      plugin: plugins.cbba.cbba.CBBA