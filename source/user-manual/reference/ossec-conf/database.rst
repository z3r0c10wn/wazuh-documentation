.. Copyright (C) 2019 Wazuh, Inc.

.. _reference_database:

database
========

.. topic:: XML section name

	.. code-block:: xml

		<database>
		</database>

This section shows how to configure the options for the Wazuh database management.

Options
-------

- `worker_pool_size`_
- `commit_time`_
- `open_db_limit`_
- `rlimit_nofile`_
- `thread_stack_size`_
- `log_level`_

Subsections
-----------

- :ref:`global_db <reference_database_global>`

.. _reference_database_global:

Global DB subsection options
----------------------------

- `sync_agents`_
- `sync_rootcheck`_
- `full_sync`_
- `real_time`_
- `interval`_
- `max_queued_events`_

To disable the Wazuh Database Synchronization Module, the sync directives must be set to 0 in the ``etc/ossec.conf`` file as shown below:

.. code-block:: xml

  <database>
    <global_db>
      <sync_agents>0</sync_agents>
      <sync_rootcheck>0</sync_rootcheck>
    </global_db>
  </database>

With the above settings, the Database Synchronization Module will not be loaded when Wazuh starts.

sync_agents
^^^^^^^^^^^

Toggles synchronization of agent database with client.keys on or off.

+--------------------+------------------------------------+
| **Default value**  | 1                                  |
+--------------------+------------------------------------+
| **Allowed values** | 0: Disable                         |
+                    +------------------------------------+
|                    | 1: Enable                          |
+--------------------+------------------------------------+

sync_rootcheck
^^^^^^^^^^^^^^

Toggles synchronization of policy monitoring data with Rootcheck database on or off.

+--------------------+------------------------------------+
| **Default value**  | 1                                  |
+--------------------+------------------------------------+
| **Allowed values** | 0: Disable                         |
+                    +------------------------------------+
|                    | 1: Enable                          |
+--------------------+------------------------------------+

full_sync
^^^^^^^^^

Toggles full data synchronization on or off.

+--------------------+------------------------------------+
| **Default value**  | 0                                  |
+--------------------+------------------------------------+
| **Allowed values** | 0: Disable                         |
+                    +------------------------------------+
|                    | 1: Enable                          |
+--------------------+------------------------------------+

real_time
^^^^^^^^^

Toggles synchronization of data in real-time (supported on Linux only) on and off.

+--------------------+------------------------------------+
| **Default value**  | 0                                  |
+--------------------+------------------------------------+
| **Allowed values** | 0: Disable                         |
+                    +------------------------------------+
|                    | 1: Enable                          |
+--------------------+------------------------------------+

interval
^^^^^^^^

Time interval between cycles (used only if real time disabled).

+--------------------+------------------------------------+
| **Default value**  | 6                                  |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 0 to 86400.        |
+--------------------+------------------------------------+

max_queued_events
^^^^^^^^^^^^^^^^^

Maximum number of queued events (only used if *inotify* is available).

+--------------------+-------------------------------------+
| **Default value**  | 0                                   |
+--------------------+-------------------------------------+
| **Allowed values** | 0: Use system default               |
+                    +-------------------------------------+
|                    | 1: Any number from 0 to 2147483647. |
+--------------------+-------------------------------------+

Options
-------

worker_pool_size
^^^^^^^^^^^^^^^^

Number of worker threads.

+--------------------+------------------------------------+
| **Default value**  | 8                                  |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 1 to 32.           |
+--------------------+------------------------------------+

commit_time
^^^^^^^^^^^

Time margin before committing to the database (seconds).

+--------------------+------------------------------------+
| **Default value**  | 60                                 |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 10 to 3600.        |
+--------------------+------------------------------------+

open_db_limit
^^^^^^^^^^^^^

Number of allowed open databases before closing.

+--------------------+------------------------------------+
| **Default value**  | 64                                 |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 1 to 4096.         |
+--------------------+------------------------------------+

rlimit_nofile
^^^^^^^^^^^^^

Maximum number of file descriptor that WazuhDB can open.

+--------------------+------------------------------------+
| **Default value**  | 65536                              |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 1024 to 1048576.   |
+--------------------+------------------------------------+

thread_stack_size
^^^^^^^^^^^^^^^^^

Defines the stack size for child threads created by the database process in KiB.

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

  <database>
    <!-- Global DB options -->
    <global_db>
      <sync_agents>1</sync_agents>
      <sync_rootcheck>1</sync_rootcheck>
      <full_sync>0</full_sync>
      <real_time>1</real_time>
      <interval>60</interval>
      <max_queued_events>0</max_queued_events>
    </global_db>

    <!-- Wazuh DB options -->
    <worker_pool_size>8</worker_pool_size>
    <commit_time>60</commit_time>
    <open_db_limit>64</open_db_limit>
    <rlimit_nofile>65536</rlimit_nofile>
    <log_level>0</log_level>
  </database>