.. Copyright (C) 2019 Wazuh, Inc.

.. _reference_execute:

execute
=======

.. topic:: XML section name

	.. code-block:: xml

		<execute>
		</execute>

This section shows how to configure the options for :doc:`execd <../daemons/ossec-execd>`. This section is related to :ref:`Active response <reference_ossec_active_response>`.

Options
-------

- `request_timeout`_
- `max_restart_lock`_
- `log_level`_

request_timeout
^^^^^^^^^^^^^^^

Timeout to execute remote requests (seconds).

+--------------------+--------------------------------------+
| **Default value**  | 60                                   |
+--------------------+--------------------------------------+
| **Allowed values** | Any number between 1 and 3600.       |
+--------------------+--------------------------------------+

.. _reference_execute_max_restart_lock:

max_restart_lock
^^^^^^^^^^^^^^^^

Maximum timeout that the agent cannot restart while updating (seconds).

+--------------------+--------------------------------------+
| **Default value**  | 600                                  |
+--------------------+--------------------------------------+
| **Allowed values** | Any number between 0 and 300.        |
+--------------------+--------------------------------------+

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

  <execute>
    <request_timeout>60</request_timeout>
    <max_restart_lock>600</max_restart_lock>
    <log_level>0</log_level>
  </execute>