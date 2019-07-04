.. Copyright (C) 2019 Wazuh, Inc.

.. _reference_modules:

modules
=======

.. topic:: XML section name

	.. code-block:: xml

		<modules>
		</modules>

This section shows how to configure the common options for ``wazuh modules``. This affects all wodles, ``SCA``, ``Fluent-Forward`` and ``Download`` module.

Options
-------

- `task_nice`_
- `max_eps`_
- `kill_timeout`_
- `thread_stack_size`_
- `log_level`_

task_nice
^^^^^^^^^

Indicates the priority of the tasks. The lower the value, the higher the priority.

+--------------------+--------------------------------------+
| **Default value**  | 10                                   |
+--------------------+--------------------------------------+
| **Allowed values** | Any number between -20 and 19.       |
+--------------------+--------------------------------------+

.. _reference_modules_max_eps:

max_eps
^^^^^^^

Maximum number of events per second sent by each module.

+--------------------+--------------------------------------+
| **Default value**  | 100                                  |
+--------------------+--------------------------------------+
| **Allowed values** | Any number between 1 and 1000.       |
+--------------------+--------------------------------------+

kill_timeout
^^^^^^^^^^^^

Time for a process to quit before killing it.

+--------------------+--------------------------------------+
| **Default value**  | 10                                   |
+--------------------+--------------------------------------+
| **Allowed values** | Any number between 0 and 3600.       |
+--------------------+--------------------------------------+

thread_stack_size
^^^^^^^^^^^^^^^^^

Defines the stack size for child threads created by the modules process in KiB.

+--------------------+------------------------------------------------------------------------------------------+
| **Default value**  | 8192                                                                                     |
+--------------------+------------------------------------------------------------------------------------------+
| **Allowed values** | Any integer between 2048 and 65536                                                       |
+--------------------+------------------------------------------------------------------------------------------+

log_level
^^^^^^^^^

Debug options. Indicates the level of detail in the ouput log ``ossec.log``.

+--------------------+------------------------------------+
| **Default value**  | 0                                  |
+--------------------+------------------------------------+
| **Allowed values** | 0: No debug output                 |
+                    +------------------------------------+
|                    | 1: Standard debug output           |
+                    +------------------------------------+
|                    | 2: Verbose debug output            |
+--------------------+------------------------------------+

Example configuration
---------------------

This is an example of configuration of this section with the default values set (it has the same effect as not setting this block):

.. code-block:: xml

  <modules>
    <task_nice>10</task_nice>
    <max_eps>100</max_eps>
    <kill_timeout>10</kill_timeout>
    <thread_stack_size>8192</thread_stack_size>
    <log_level>0</log_level>
  </modules>