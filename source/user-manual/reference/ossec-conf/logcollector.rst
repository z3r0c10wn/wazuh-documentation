.. Copyright (C) 2019 Wazuh, Inc.

.. _reference_logcollector:

logcollector
============

.. topic:: XML section name

	.. code-block:: xml

		<logcollector>
		</logcollector>

This section shows how to configure the common options for logcollector (localfile).

Subsections
-----------

- :ref:`files <logcollector_files>`
- :ref:`reload <logcollector_reload>`

Options
-------

- `remote_commands`_
- `sock_fail_time`_
- `queue_size`_
- `sample_log_length`_
- `log_level`_

.. _reference_logcollector_remote_commands:

remote_commands
^^^^^^^^^^^^^^^

Enable it to accept execute commands pushed from the manager in the shared configuration.

+--------------------+------------------------------------+
| **Default value**  | 0                                  |
+--------------------+------------------------------------+
| **Allowed values** | 0: Disable                         |
+                    +------------------------------------+
|                    | 1: Enable                          |
+--------------------+------------------------------------+

sock_fail_time
^^^^^^^^^^^^^^

Time to reattempt a socket connection after a failure (seconds).

+--------------------+--------------------------------------+
| **Default value**  | 300                                  |
+--------------------+--------------------------------------+
| **Allowed values** | Any number between 1 and 3600.       |
+--------------------+--------------------------------------+

queue_size
^^^^^^^^^^

Queue size for each type of socket.

+--------------------+--------------------------------------+
| **Default value**  | 1024                                 |
+--------------------+--------------------------------------+
| **Allowed values** | Any number between 128 and 220000.   |
+--------------------+--------------------------------------+

sample_log_length
^^^^^^^^^^^^^^^^^

Sample log length limit for errors about large message. This truncates the output error message to the characters indicated in this option.

+--------------------+--------------------------------------+
| **Default value**  | 64                                   |
+--------------------+--------------------------------------+
| **Allowed values** | Any number between 1 and 4096.       |
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

.. _logcollector_files:

Files subsection
----------------

- `loop_timeout`_
- `open_attempts`_
- `vcheck`_
- `max_lines`_
- `max_files`_
- `input_threads`_
- `rlimit_nofile`_
- `exclude_interval`_

loop_timeout
^^^^^^^^^^^^

File polling interval.

+--------------------+--------------------------------------+
| **Default value**  | 2                                    |
+--------------------+--------------------------------------+
| **Allowed values** | Any number between 1 and 120.        |
+--------------------+--------------------------------------+

open_attempts
^^^^^^^^^^^^^

Number of attempts to open a log file.

+--------------------+--------------------------------------+
| **Default value**  | 8                                    |
+--------------------+--------------------------------------+
| **Allowed values** | Any number between 0 and 998.        |
+--------------------+--------------------------------------+

.. _reference_logcollector_vcheck:

vcheck
^^^^^^

File checking interval.

+--------------------+--------------------------------------+
| **Default value**  | 64                                   |
+--------------------+--------------------------------------+
| **Allowed values** | Any number between 0 and 1024.       |
+--------------------+--------------------------------------+

.. _reference_logcollector_max_lines:

max_lines
^^^^^^^^^

Maximum number of lines to read from the same file.

+--------------------+--------------------------------------+
| **Default value**  | 10000                                |
+--------------------+--------------------------------------+
| **Allowed values** | 0: Disable line burst limitation     |
+                    +--------------------------------------+
|                    | Any number between 1 and 1000000.    |
+--------------------+--------------------------------------+

max_files
^^^^^^^^^

Maximum number of files to be monitored.

+--------------------+--------------------------------------+
| **Default value**  | 1000                                 |
+--------------------+--------------------------------------+
| **Allowed values** | Any number between 1 and 100000.     |
+--------------------+--------------------------------------+

input_threads
^^^^^^^^^^^^^

Number of input threads for reading files.

+--------------------+--------------------------------------+
| **Default value**  | 4                                    |
+--------------------+--------------------------------------+
| **Allowed values** | Any number between 1 and 128.        |
+--------------------+--------------------------------------+

rlimit_nofile
^^^^^^^^^^^^^

Maximum number of file descriptor that Logcollector can open. This value must be higher than *max_files*.

+--------------------+--------------------------------------+
| **Default value**  | 1100                                 |
+--------------------+--------------------------------------+
| **Allowed values** | Any number between 1024 and 1048576. |
+--------------------+--------------------------------------+

exclude_interval
^^^^^^^^^^^^^^^^

Excluded files refresh interval (seconds).

+--------------------+--------------------------------------+
| **Default value**  | 86400                                |
+--------------------+--------------------------------------+
| **Allowed values** | Any number between 1 and 172800.     |
+--------------------+--------------------------------------+


.. _logcollector_reload:

Reload subsection options
-------------------------

- `force`_
- `interval`_
- `delay`_

force
^^^^^

Force file handler reloading: close and reopen monitored files.

+--------------------+------------------------------------+
| **Default value**  | 0                                  |
+--------------------+------------------------------------+
| **Allowed values** | 0: Disable                         |
+                    +------------------------------------+
|                    | 1: Enable                          |
+--------------------+------------------------------------+

interval
^^^^^^^^

File reloading interval (seconds). This will only apply if the option *force* is enabled. This interval must be greater or equal than *vcheck*.

+--------------------+--------------------------------------+
| **Default value**  | 64                                   |
+--------------------+--------------------------------------+
| **Allowed values** | Any number between 1 and 86400.      |
+--------------------+--------------------------------------+

delay
^^^^^

File reloading delay (between close and open), in milliseconds

+--------------------+--------------------------------------+
| **Default value**  | 1000                                 |
+--------------------+--------------------------------------+
| **Allowed values** | Any number between 0 and 30000.      |
+--------------------+--------------------------------------+

Example configuration
---------------------

This is an example of configuration of this section with the default values set (it has the same effect as not setting this block):

.. code-block:: xml

  <logcollector>
    <remote_commands>0</remote_commands>
    <sock_fail_time>300</sock_fail_time>
    <queue_size>1024</queue_size>
    <sample_log_length>64</sample_log_length>
    <files>
      <loop_timeout>2</loop_timeout>
      <open_attempts>8</open_attempts>
      <vcheck>64</vcheck>
      <max_lines>10000</max_lines>
      <max_files>1000</max_files>
      <input_threads>4</input_threads>
      <rlimit_nofile>1100</rlimit_nofile>
      <exclude_interval>86400</exclude_interval>
    </files>
    <reload>
      <force>0</force>
      <interval>64</interval>
      <delay>1000</delay>
     </reload>
     <log_level>0</log_level>
  </logcollector>

