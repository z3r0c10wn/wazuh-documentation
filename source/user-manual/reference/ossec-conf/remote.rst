.. Copyright (C) 2019 Wazuh, Inc.

.. _reference_ossec_remote:

remote
=======

.. topic:: XML section name

	.. code-block:: xml

		<remote>
		</remote>

Configuration of manager to listen for events from the agents.

Options
-------

- `connection`_
- `port`_
- `protocol`_
- `allowed-ips`_
- `denied-ips`_
- `local_ip`_
- `ipv6`_
- `queue_size`_
- `recv_counter_flush`_
- `comp_avg_printout`_
- `verify_msg_id`_
- `pass_empty_keyfile`_
- `rlimit_nofile`_
- `thread_stack_size`_
- `log_level`_

connection
^^^^^^^^^^^

Specifies a type of incoming connection to accept: secure or syslog.

+--------------------+----------------+
| **Default value**  | secure         |
+--------------------+----------------+
| **Allowed values** | secure, syslog |
+--------------------+----------------+

port
^^^^^^^^^^^

Specifies the port to use to listen for events.

+--------------------+---------------------------------+
| **Default value**  | 1514 if secure, 514 if syslog   |
+--------------------+---------------------------------+
| **Allowed values** | Any port number from 1 to 65535 |
+--------------------+---------------------------------+

.. _manager_protocol:

protocol
^^^^^^^^^^^

Specifies the protocol to use. It is available for secure connections and syslog events.

+--------------------+----------+
| **Default value**  | udp      |
+--------------------+----------+
| **Allowed values** | udp, tcp |
+--------------------+----------+

.. note::
	It is not possible to use both protocols simultaneously.

allowed-ips
^^^^^^^^^^^

List of IP addresses that are allowed to send syslog messages to the server (one per line).

+--------------------+---------------------------+
| **Default value**  | n/a                       |
+--------------------+---------------------------+
| **Allowed values** | Any IP address or network |
+--------------------+---------------------------+

.. note::

   It is necessary to list at least one IP address when using the syslog connection type.

denied-ips
^^^^^^^^^^^

List of IP addresses that are not allowed to send syslog messages to the server (one per line).

+--------------------+---------------------------+
| **Default value**  | n/a                       |
+--------------------+---------------------------+
| **Allowed values** | Any IP address or network |
+--------------------+---------------------------+


local_ip
^^^^^^^^^^^

Local ip address to use to listen for connections.

+--------------------+-------------------------+
| **Default value**  | All interfaces          |
+--------------------+-------------------------+
| **Allowed values** | Any internal ip address |
+--------------------+-------------------------+


ipv6
^^^^^^^^^^^

Whether the local IP address is IPv6

+--------------------+------------------+
| **Default value**  | no               |
+--------------------+------------------+
| **Allowed values** | yes, no          |
+--------------------+------------------+

.. note::

  Currently it's not possible to set both *local_ip* and *ipv6*

queue_size
^^^^^^^^^^^^

Sets the capacity of the remote daemon queue in number of agent events.

+--------------------+----------------------------------+
| **Default value**  | 131072                           |
+--------------------+----------------------------------+
| **Allowed values** | Any number between 1 and 262144. |
+--------------------+----------------------------------+

.. note::
  The remote queue is only available for agent events, not *syslog* events. This options only works when the **connection** is set to ``secure``.

recv_counter_flush
^^^^^^^^^^^^^^^^^^

Flush rate for the receive counter.

+--------------------+-----------------------------------+
| **Default value**  | 128                               |
+--------------------+-----------------------------------+
| **Allowed values** | Any number between 10 and 999999. |
+--------------------+-----------------------------------+

comp_avg_printout
^^^^^^^^^^^^^^^^^

Compression averages printout.

+--------------------+-----------------------------------+
| **Default value**  | 19999                             |
+--------------------+-----------------------------------+
| **Allowed values** | Any number between 10 and 999999. |
+--------------------+-----------------------------------+

verify_msg_id
^^^^^^^^^^^^^

Toggle to enable or disable verification of message id.

+--------------------+------------------------------------+
| **Default value**  | 0                                  |
+--------------------+------------------------------------+
| **Allowed values** | 0: Disable                         |
+                    +------------------------------------+
|                    | 1: Enable                          |
+--------------------+------------------------------------+

pass_empty_keyfile
^^^^^^^^^^^^^^^^^^

Toggle to enable or disable acceptance of empty client.keys.

+--------------------+------------------------------------+
| **Default value**  | 1                                  |
+--------------------+------------------------------------+
| **Allowed values** | 0: Disable                         |
+                    +------------------------------------+
|                    | 1: Enable                          |
+--------------------+------------------------------------+

rlimit_nofile
^^^^^^^^^^^^^

Maximum number of file descriptor that Remoted can open

+--------------------+--------------------------------------+
| **Default value**  | 65536                                |
+--------------------+--------------------------------------+
| **Allowed values** | Any number between 1024 and 1048576. |
+--------------------+--------------------------------------+

thread_stack_size
^^^^^^^^^^^^^^^^^

Defines the stack size for child threads created by the remote process in KiB.

+--------------------+------------------------------------------------------------------------------------------+
| **Default value**  | 8192                                                                                     |
+--------------------+------------------------------------------------------------------------------------------+
| **Allowed values** | Any integer between 2048 and 65536                                                       |
+--------------------+------------------------------------------------------------------------------------------+

log_level
^^^^^^^^^

Debug options. Indicates the level of detail in the ouput log ``ossec.log``. Only for manager.

+--------------------+------------------------------------+
| **Default value**  | 0                                  |
+--------------------+------------------------------------+
| **Allowed values** | 0: No debug output                 |
+                    +------------------------------------+
|                    | 1: Standard debug output           |
+                    +------------------------------------+
|                    | 2: Verbose debug output            |
+--------------------+------------------------------------+

Subsections
-----------

- :ref:`pool <remote_pool>`
- :ref:`timeout <remote_timeout>`
- :ref:`request <remote_request>`
- :ref:`shared <remote_shared>`
- :ref:`interval <remote_interval>`
- :ref:`group <remote_group>`
- :ref:`memory <remote_memory>`
- :ref:`tcp <remote_tcp>`

.. _remote_pool:

Pool subsection options
------------------------

- `sender`_
- :ref:`request <request_pool>`
- `worker`_

sender
^^^^^^

Number of parallel threads to send the shared file.

+--------------------+------------------------------------+
| **Default value**  | 8                                  |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 1 to 64.           |
+--------------------+------------------------------------+

.. _request_pool:

request
^^^^^^^

Number of parallel threads to dispatch requests.

+--------------------+------------------------------------+
| **Default value**  | 1024                               |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 1 to 4096.         |
+--------------------+------------------------------------+

worker
^^^^^^

Number of threads that process the payload reception.

+--------------------+------------------------------------+
| **Default value**  | 4                                  |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 1 to 16.           |
+--------------------+------------------------------------+

.. _remote_timeout:

Timeout subsection options
--------------------------

- `max_attempts`_
- :ref:`request <request_timeout>`
- `response`_
- `recv`_
- `send`_

max_attempts
^^^^^^^^^^^^

Maximum number of sending attempts.

+--------------------+------------------------------------+
| **Default value**  | 4                                  |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 1 to 16.           |
+--------------------+------------------------------------+

.. _request_timeout:

request
^^^^^^^

Timeout to reject a new request (seconds).

+--------------------+------------------------------------+
| **Default value**  | 10                                 |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 1 to 600.          |
+--------------------+------------------------------------+

response
^^^^^^^^

Timeout for request responses (seconds).

+--------------------+------------------------------------+
| **Default value**  | 60                                 |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 1 to 3600.         |
+--------------------+------------------------------------+

recv
^^^^

Maximum time waiting for a client response in TCP (seconds).

+--------------------+------------------------------------+
| **Default value**  | 1                                  |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 1 to 60.           |
+--------------------+------------------------------------+

send
^^^^

Maximum time waiting for a client delivery in TCP (seconds).

+--------------------+------------------------------------+
| **Default value**  | 1                                  |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 1 to 60.           |
+--------------------+------------------------------------+

.. _remote_request:

Request subsection options
--------------------------

- `rto_sec`_
- `rto_msec`_


rto_sec
^^^^^^^^

Retransmission timeout seconds.

+--------------------+------------------------------------+
| **Default value**  | 1                                  |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 0 to 60.           |
+--------------------+------------------------------------+

rto_msec
^^^^^^^^

Retransmission timeout milliseconds.

+--------------------+------------------------------------+
| **Default value**  | 0                                  |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 0 to 999.          |
+--------------------+------------------------------------+

.. _remote_shared:

Shared subsection options
-------------------------

- `merge`_
- `reload`_

merge
^^^^^^

Merge shared configuration to be broadcasted to agents

+--------------------+------------------------------------+
| **Default value**  | 1                                  |
+--------------------+------------------------------------+
| **Allowed values** | 0: Disable shared configuration    |
+                    +------------------------------------+
|                    | 1: Enable shared configuration     |
+--------------------+------------------------------------+

reload
^^^^^^

Time (seconds) between reloading of shared files.

+--------------------+------------------------------------+
| **Default value**  | 10                                 |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 1 to 18000.        |
+--------------------+------------------------------------+

.. _remote_interval:

Interval subsection options
---------------------------

.. _reference_ossec_remote_state_interval:

state
^^^^^

Interval between the updates of the status file (seconds).

+--------------------+------------------------------------+
| **Default value**  | 5                                  |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 0 to 86400.        |
+--------------------+------------------------------------+

keyupdate
^^^^^^^^^

Keys file reloading latency (seconds).

+--------------------+------------------------------------+
| **Default value**  | 10                                 |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 1 to 3600.         |
+--------------------+------------------------------------+

.. _remote_group:

Group subsection options
------------------------

guess_agent
^^^^^^^^^^^

Guess the group to which the agent belongs.

+--------------------+------------------------------------+
| **Default value**  | 0                                  |
+--------------------+------------------------------------+
| **Allowed values** | 0: Do not guess group              |
+                    +------------------------------------+
|                    | 1: Guess group agent               |
+--------------------+------------------------------------+

data_flush
^^^^^^^^^^

Cleans residual data from unused groups/multigroups. Time (seconds) between cleanings.

+--------------------+------------------------------------+
| **Default value**  | 86400                              |
+--------------------+------------------------------------+
| **Allowed values** | 0: Never clean up residual data    |
+                    +------------------------------------+
|                    | Any number from 1 to 2592000.      |
+--------------------+------------------------------------+

.. _remote_memory:

Memory subsection options
-------------------------

receive_chunk
^^^^^^^^^^^^^

Receiving chunk size for TCP. Powers of two are suggested.

+--------------------+------------------------------------+
| **Default value**  | 4096                               |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 1024 to 16384.     |
+--------------------+------------------------------------+

buffer_relax
^^^^^^^^^^^^

Method for memory deallocation after accepting input data. This option applies in TCP mode only.

+--------------------+--------------------------------------------+
| **Default value**  | 0                                          |
+--------------------+--------------------------------------------+
| **Allowed values** | 0: Keep the memory for each TCP session.   |
+                    +--------------------------------------------+
|                    | 1: Shrink memory back to ``receive_chunk`` |
+                    +--------------------------------------------+
|                    | 2: Fully deallocate memory after usage.    |
+--------------------+--------------------------------------------+

.. _remote_tcp:

TCP subsection options
----------------------

keepidle
^^^^^^^^

Time (in seconds) the connection needs to remain idle before TCP starts sending keepalive probes.

+--------------------+------------------------------------+
| **Default value**  | 30                                 |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 1 to 7200.         |
+--------------------+------------------------------------+

keepintvl
^^^^^^^^^

Time (in seconds) between individual keepalive probes.

+--------------------+------------------------------------+
| **Default value**  | 10                                 |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 1 to 100.          |
+--------------------+------------------------------------+

keepcnt
^^^^^^^

Maximum number of keepalive probes TCP should send before dropping the connection.

+--------------------+------------------------------------+
| **Default value**  | 3                                  |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 1 to 50.           |
+--------------------+------------------------------------+

Example of configuration
------------------------

.. code-block:: xml

    <remote>
      <connection>syslog</connection>
      <port>514</port>
      <protocol>udp</protocol>
      <allowed-ips>192.168.1.0/24</allowed-ips>
      <local_ip>192.168.1.5</local_ip>
    </remote>

    <remote>
      <connection>secure</connection>
      <port>1514</port>
      <protocol>udp</protocol>
      <queue_size>16384</queue_size>
    </remote>
