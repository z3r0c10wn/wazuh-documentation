.. Copyright (C) 2019 Wazuh, Inc.

.. _ossec_remoted_state_file:

ossec-remoted.state
===================

The statistical file for **ossec-remoted** is located at ``/var/ossec/var/run/ossec-remoted.state``.

This file provides information about the remote daemon as the queue size, discarded messages, number of remote connections and other useful information. 

By default, this file is updated every 5 seconds. This interval can be changed by modifying the option :ref:`state_interval <reference_ossec_remote_state_interval>` in the ``ossec.conf`` file.

Below there is an example of the content of the file:

.. code-block:: bash

    # State file for ossec-remoted
    # Updated every 5 seconds.

    # Queue size
    queue_size='0'

    # Total queue size
    total_queue_size='131072'

    # TCP sessions
    tcp_sessions='130'

    # Events sent to Analysisd
    evt_count='19097'

    # Control messages received
    ctrl_msg_count='3444'

    # Discarded messages
    discarded_count='23'

    # Messages sent
    msg_sent='3460'

    # Total number of bytes received
    recv_bytes='435879'
