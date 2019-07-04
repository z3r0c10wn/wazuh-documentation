.. Copyright (C) 2019 Wazuh, Inc.

.. _reference_ossec_client:

client
======

.. topic:: XML section name

	.. code-block:: xml

		<client>
		</client>

This section explains how to configure the connection to the manager.

Subsections
-----------

- `server`_
- :ref:`request <reference_ossec_client_request>`

server
^^^^^^

.. versionadded:: 3.0.0

Configures the connection parameters for each server an agent connects to.

Server subsection options
-------------------------

- `address`_
- :ref:`port <server_port>`
- :ref:`protocol <server_protocol>`

address
^^^^^^^^

Specifies the IP address or the hostname of the Wazuh manager.

+--------------------+-------------------------------------------------------------+
| **Default value**  | n/a                                                         |
+--------------------+-------------------------------------------------------------+
| **Allowed values** | Any valid IP address or any resolvable hostname is allowed. |
+--------------------+-------------------------------------------------------------+

.. _server_port:

port
^^^^

Specifies the port to send events to on the manager.  This must match the associated listening port configured on the Wazuh manager.

+--------------------+---------------------------------------------+
| **Default value**  | 1514                                        |
+--------------------+---------------------------------------------+
| **Allowed values** | Any port number from 1 to 65535 is allowed. |
+--------------------+---------------------------------------------+

.. _server_protocol:

protocol
^^^^^^^^

Specifies the protocol to use when connecting to the manager.

+--------------------+----------+
| **Default value**  | udp      |
+--------------------+----------+
| **Allowed values** | udp, tcp |
+--------------------+----------+

Options
-------

- :ref:`server-ip <legacy_server-ip>`
- :ref:`server-hostname <legacy_server-hostname>`
- :ref:`port <legacy_port>`
- :ref:`protocol <legacy_protocol>`
- `config-profile`_
- `notify_time`_
- `time-reconnect`_
- `local_ip`_
- `disable-active-response`_
- `auto_restart`_
- `crypto_method`_
- `state_interval`_
- `recv_timeout`_
- `remote_conf`_
- `max_attempts`_
- `recv_counter_flush`_
- `comp_avg_printout`_
- `verify_msg_id`_
- `thread_stack_size`_
- `log_level`_

.. _legacy_server-ip:

server-ip
^^^^^^^^^

.. deprecated:: 3.0.0

Specifies the IP address of the Wazuh manager.

+--------------------+----------------------------------+
| **Default value**  | n/a                              |
+--------------------+----------------------------------+
| **Allowed values** | Any valid IP address is allowed. |
+--------------------+----------------------------------+


.. _legacy_server-hostname:

server-hostname
^^^^^^^^^^^^^^^

.. deprecated:: 3.0.0

Specifies the hostname of the Wazuh manager.

+--------------------+-------------------------------------+
| **Default value**  | n/a                                 |
+--------------------+-------------------------------------+
| **Allowed values** | Any resolvable hostname is allowed. |
+--------------------+-------------------------------------+

.. warning::
		This parameter is incompatible with `server-ip`_. Since version 3.0, these fields have been merged into a single field called `address` that accepts both formats.

.. _legacy_port:

port
^^^^

.. deprecated:: 3.0.0

Specifies the port on the manager to send events to.  This must match the associated listening port configured on the Wazuh manager.

+--------------------+---------------------------------------------+
| **Default value**  | 1514                                        |
+--------------------+---------------------------------------------+
| **Allowed values** | Any port number from 1 to 65535 is allowed. |
+--------------------+---------------------------------------------+

.. _legacy_protocol:

protocol
^^^^^^^^

.. deprecated:: 3.0.0

Specifies the protocol to use when connecting to manager.

+--------------------+----------+
| **Default value**  | udp      |
+--------------------+----------+
| **Allowed values** | udp, tcp |
+--------------------+----------+

.. _reference_ossec_client_config_profile:

config-profile
^^^^^^^^^^^^^^

Specifies the ``agent.conf`` profile(s) to be used by the agent.

+--------------------+----------------------------------------------------------------------+
| **Default value**  | n/a                                                                  |
+--------------------+----------------------------------------------------------------------+
| **Allowed values** | Multiple profiles can be included, separated by a comma and a space. |
+--------------------+----------------------------------------------------------------------+


notify_time
^^^^^^^^^^^

Specifies the time in seconds between agent checkins to the manager.  More frequent checkins speed up dissemination of an updated ``agent.conf`` file to the agents, but may also put an undo load on the manager if there are a large number of agents.

+--------------------+-----------------------------+
| **Default value**  | 10                          |
+--------------------+-----------------------------+
| **Allowed values** | A positive number (seconds) |
+--------------------+-----------------------------+


time-reconnect
^^^^^^^^^^^^^^

Specifies the time in seconds before a reconnection is attempted. This should be set to a higher number than the ``notify_time`` parameter.

For example, a ``notify_time`` setting of 60 combined with a time-reconnect of 300 would mean that agents will attempt to check in once per minute, but if a checkin attempt fails to get a response from the manager, the agent will wait five minutes before trying again.  Checkins will resume their normal one-minute interval following a successful connection attempt.

+--------------------+-----------------------------+
| **Default value**  | 60                          |
+--------------------+-----------------------------+
| **Allowed values** | A positive number (seconds) |
+--------------------+-----------------------------+

.. warning::
	Notice that the ``notify_time`` value uses an underscore while the ``time-reconnect`` value uses a dash.  This is an unfortunate legacy naming inconsistency that is easy to mix up.

local_ip
^^^^^^^^

Specifies which IP address will be used to communicate with the manager when the agent has multiple network interfaces.

+--------------------+----------------------------------+
| **Default value**  | n/a                              |
+--------------------+----------------------------------+
| **Allowed values** | Any valid IP address is allowed. |
+--------------------+----------------------------------+

disable-active-response
^^^^^^^^^^^^^^^^^^^^^^^

**Deprecated:**

.. warning::

        This is an obsolete method to disable active response. The recommended way is by configuring as shown in the :doc:`active-response <active-response>` section.

+--------------------+---------------------+
| **Default value**  | no                  |
+--------------------+---------------------+
| **Allowed values** | yes, no             |
+--------------------+---------------------+

auto_restart
^^^^^^^^^^^^

Toggles on and off the automatic restart of agents when a new valid configuration is received from the manager.

+--------------------+---------------------+
| **Default value**  | yes                 |
+--------------------+---------------------+
| **Allowed values** | yes, no             |
+--------------------+---------------------+

crypto_method
^^^^^^^^^^^^^

.. versionadded:: 3.5.0

Choose the encryption of the messages that the agent sends to the manager.

+--------------------+---------------------+
| **Default value**  | aes                 |
+--------------------+---------------------+
| **Allowed values** | blowfish, aes       |
+--------------------+---------------------+

.. _reference_ossec_agent_state_interval:

state_interval
^^^^^^^^^^^^^^

Interval for agent status file updating (seconds).

+--------------------+--------------------------------------------+
| **Default value**  | 5                                          |
+--------------------+--------------------------------------------+
| **Allowed values** | 0: Disabled                                |
+                    +--------------------------------------------+
|                    | Any number between 0 and 86400.            |
+--------------------+--------------------------------------------+

recv_timeout
^^^^^^^^^^^^

Maximum time waiting for a server response in TCP (seconds).

+--------------------+--------------------------------------+
| **Default value**  | 60                                   |
+--------------------+--------------------------------------+
| **Allowed values** | Any number between 1 and 600.        |
+--------------------+--------------------------------------+

remote_conf
^^^^^^^^^^^

Apply or refuse remote configuration. If disabled, the agent won't load the shared configuration pushed by the manager.

+--------------------+------------------------------------+
| **Default value**  | 1                                  |
+--------------------+------------------------------------+
| **Allowed values** | 0: Disable shared configuration    |
+                    +------------------------------------+
|                    | 1: Enable shared configuration     |
+--------------------+------------------------------------+

.. warning::
   This option cannot be changed via shared configuration (``agent.conf``) for security reasons.

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

max_attempts
^^^^^^^^^^^^

Maximum number of sending attempts.

+--------------------+------------------------------------+
| **Default value**  | 4                                  |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 1 to 16.           |
+--------------------+------------------------------------+

thread_stack_size
^^^^^^^^^^^^^^^^^

Defines the stack size for child threads created by the agent process in KiB.

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

.. _reference_ossec_client_request:

Request subsection options
--------------------------

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

pool
^^^^

Number of parallel threads to dispatch requests.

+--------------------+------------------------------------+
| **Default value**  | 1024                               |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 1 to 4096.         |
+--------------------+------------------------------------+

Sample configuration
--------------------

.. code-block:: xml

    <client>
      <server>
        <address>192.168.1.100</address>
        <port>1514</port>
        <protocol>tcp</protocol>
      </server>
      <server>
        <address>example.hostname</address>
        <protocol>udp</protocol>
      </server>
      <config-profile>webserver, debian8</config-profile>
      <notify_time>30</notify_time>
      <time-reconnect>120</time-reconnect>
      <auto_restart>yes</auto_restart>
    </client>
