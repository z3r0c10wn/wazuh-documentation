.. Copyright (C) 2019 Wazuh, Inc.

.. _reference__ossec_analysis:

analysis
=============

.. topic:: XML section name

	.. code-block:: xml

		<analysis>
		</analysis>

Configuration options for analysis.

Subsections
-----------

- :ref:`stats <stats>`
- :ref:`fts <fts>`
- :ref:`labels <analysis_labels>`
- :ref:`threads <analysis_threads>`
- :ref:`queue_size <analysis_queue_size>`

.. _stats:

Stats subsection options
------------------------

- `maxdiff`_
- `mindiff`_
- `percent_diff`_

maxdiff
^^^^^^^

This is the maximum difference between the average alerts received in an hour and the actual alerts received that's need to trigger an alert.

+--------------------+------------------------------------+
| **Default value**  | 999000                             |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 1 to 999999.       |
+--------------------+------------------------------------+

mindiff
^^^^^^^

This is the minimum difference between the average alerts received in an hour and the actual alerts received that's need to trigger an alert.

+--------------------+------------------------------------+
| **Default value**  | 1250                               |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 10 to 999999.      |
+--------------------+------------------------------------+

percent_diff
^^^^^^^^^^^^

This is the percentage of the average alerts received in an hour that if surpassed by the actual alerts received will trigger an alert.

+--------------------+------------------------------------+
| **Default value**  | 150                                |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 5 to 9999.         |
+--------------------+------------------------------------+

These three options are related as described in the following formula:

.. code-block:: console

  alerts_average = 100
  percent_diff = 150
  maxdiff = 999000
  mindiff = 1250

  event_diff = (alerts_average * percent_diff) / 100 = 150

If the current alerts are more than ``alerts_average`` + ``event_diff``, it would mean the triggering of an alert but as ``event_diff`` is less than ``mindiff`` (in this case) we will trigger an alert when the current alerts generated are more than ``alerts_average`` + ``mindiff`` alerts.

.. _fts:

FTS subsection options
----------------------

list_size
^^^^^^^^^

FTS (first time seen matched rules) list maximum size.

+--------------------+------------------------------------+
| **Default value**  | 32                                 |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 12 to 512.         |
+--------------------+------------------------------------+

min_size_for_str
^^^^^^^^^^^^^^^^

FTS minimum string size. This is the string size that is compared from a FTS event with previous FTS events. 
If the event matches with at least 3 FTS events in the list, this event is ignored. 

+--------------------+------------------------------------+
| **Default value**  | 14                                 |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 6 to 128.          |
+--------------------+------------------------------------+

.. _analysis_labels:

Labels subsection options
-------------------------

cache_maxage
^^^^^^^^^^^^

Time (seconds) without reloading labels in cache from agents.

+--------------------+------------------------------------+
| **Default value**  | 1                                  |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 0 to 60.           |
+--------------------+------------------------------------+

show_hidden
^^^^^^^^^^^

Show hidden labels on alerts.

+--------------------+------------------------------------+
| **Default value**  | 0                                  |
+--------------------+------------------------------------+
| **Allowed values** | 0: Don't show hidden labels        |
+                    +------------------------------------+
|                    | 1: Show hidden labels              |
+--------------------+------------------------------------+

.. _analysis_threads:

Threads subsection options
--------------------------

event
^^^^^

Number of event decoder threads.

+--------------------+------------------------------------+
| **Default value**  | 0                                  |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 0 to 32.           |
+--------------------+------------------------------------+

syscheck
^^^^^^^^

Number of syscheck decoder threads.

+--------------------+------------------------------------+
| **Default value**  | 0                                  |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 0 to 32.           |
+--------------------+------------------------------------+

syscollector
^^^^^^^^^^^^

Number of syscollector decoder threads.

+--------------------+------------------------------------+
| **Default value**  | 0                                  |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 0 to 32.           |
+--------------------+------------------------------------+

rootcheck
^^^^^^^^^

Number of rootcheck decoder threads.

+--------------------+------------------------------------+
| **Default value**  | 0                                  |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 0 to 32.           |
+--------------------+------------------------------------+

sca
^^^

Number of SCA decoder threads.

+--------------------+------------------------------------+
| **Default value**  | 0                                  |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 0 to 32.           |
+--------------------+------------------------------------+

hostinfo
^^^^^^^^

Number of hostinfo decoder threads.

+--------------------+------------------------------------+
| **Default value**  | 0                                  |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 0 to 32.           |
+--------------------+------------------------------------+

winevent
^^^^^^^^

Number of Windows event decoder threads.

+--------------------+------------------------------------+
| **Default value**  | 0                                  |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 0 to 32.           |
+--------------------+------------------------------------+

rule_matching
^^^^^^^^^^^^^

Number of rule matching threads.

+--------------------+------------------------------------+
| **Default value**  | 0                                  |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 0 to 32.           |
+--------------------+------------------------------------+

.. _analysis_queue_size:

Queue size subsection options
-----------------------------

event
^^^^^

Event decoder queue size.

+--------------------+------------------------------------+
| **Default value**  | 16384                              |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 128 to 2000000.    |
+--------------------+------------------------------------+

syscheck
^^^^^^^^

Syscheck decoder queue size.

+--------------------+------------------------------------+
| **Default value**  | 16384                              |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 128 to 2000000.    |
+--------------------+------------------------------------+

syscollector
^^^^^^^^^^^^

Syscollector decoder queue size.

+--------------------+------------------------------------+
| **Default value**  | 16384                              |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 128 to 2000000.    |
+--------------------+------------------------------------+

rootcheck
^^^^^^^^^

Rootcheck decoder queue size.

+--------------------+------------------------------------+
| **Default value**  | 16384                              |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 128 to 2000000.    |
+--------------------+------------------------------------+

sca
^^^

SCA decoder queue size.

+--------------------+------------------------------------+
| **Default value**  | 16384                              |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 128 to 2000000.    |
+--------------------+------------------------------------+

hostinfo
^^^^^^^^

Hostinfo decoder queue size.

+--------------------+------------------------------------+
| **Default value**  | 16384                              |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 128 to 2000000.    |
+--------------------+------------------------------------+

winevent
^^^^^^^^

Windows event decoder queue size.

+--------------------+------------------------------------+
| **Default value**  | 16384                              |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 128 to 2000000.    |
+--------------------+------------------------------------+

output
^^^^^^

Output decoder queue size.

+--------------------+------------------------------------+
| **Default value**  | 16384                              |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 128 to 2000000.    |
+--------------------+------------------------------------+

archives
^^^^^^^^

Archives log queue size.

+--------------------+------------------------------------+
| **Default value**  | 16384                              |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 128 to 2000000.    |
+--------------------+------------------------------------+

statistical
^^^^^^^^^^^

Statistical log queue size.

+--------------------+------------------------------------+
| **Default value**  | 16384                              |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 128 to 2000000.    |
+--------------------+------------------------------------+

alerts
^^^^^^

Alerts log queue size.

+--------------------+------------------------------------+
| **Default value**  | 16384                              |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 128 to 2000000.    |
+--------------------+------------------------------------+

firewall
^^^^^^^^

Firewall log queue size.

+--------------------+------------------------------------+
| **Default value**  | 16384                              |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 128 to 2000000.    |
+--------------------+------------------------------------+

fts
^^^

FTS log queue size.

+--------------------+------------------------------------+
| **Default value**  | 16384                              |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 128 to 2000000.    |
+--------------------+------------------------------------+

Options
-------

- `default_timeframe`_
- `log_fw`_
- `decoder_order_size`_
- `geoip_jsonout`_
- `rlimit_nofile`_
- `min_rotate_interval`_
- `state_interval`_
- `log_level`_

.. _reference_ossec_analysis_default_timeframe:

default_timeframe
^^^^^^^^^^^^^^^^^

Default rule time-frame in seconds (time in which a rule must be executed to match).

+--------------------+------------------------------------+
| **Default value**  | 360                                |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 60 to 3600         |
+--------------------+------------------------------------+

.. _reference_ossec_analysis_log_fw:

log_fw
^^^^^^

Enable the firewall log (at ``logs/firewall/firewall.log``).

+--------------------+------------------------------------+
| **Default value**  | 1                                  |
+--------------------+------------------------------------+
| **Allowed values** | 0: Disable                         |
+                    +------------------------------------+
|                    | 1: Enable                          |
+--------------------+------------------------------------+

.. _reference_ossec_analysis_decoder_order_size:

decoder_order_size
^^^^^^^^^^^^^^^^^^

Maximum number of fields in a decoder (order tag).

+--------------------+------------------------------------+
| **Default value**  | 256                                |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 10 to 1024         |
+--------------------+------------------------------------+

.. _reference_ossec_analysis_geoip_jsonout:

geoip_jsonout
^^^^^^^^^^^^^

Enable GeoIP data at JSON alerts.

+--------------------+------------------------------------+
| **Default value**  | 1                                  |
+--------------------+------------------------------------+
| **Allowed values** | 0: Disable                         |
+                    +------------------------------------+
|                    | 1: Enable                          |
+--------------------+------------------------------------+

.. _reference_ossec_analysis_rlimit_nofile:

rlimit_nofile
^^^^^^^^^^^^^

Maximum number of file descriptor that Analysisd can open.

+--------------------+------------------------------------+
| **Default value**  | 65536                              |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 1024 to 1048576    |
+--------------------+------------------------------------+

.. _reference_ossec_analysis_min_rotate_interval:

min_rotate_interval
^^^^^^^^^^^^^^^^^^^

Minimum output rotate interval. This limits rotation by time and size.

+--------------------+------------------------------------+
| **Default value**  | 600                                |
+--------------------+------------------------------------+
| **Allowed values** | Any number from 10 to 86400        |
+--------------------+------------------------------------+

.. _reference_ossec_analysis_state_interval:

state_interval
^^^^^^^^^^^^^^

Interval for analysisd status file updating (seconds). 0 means disabled.

+--------------------+------------------------------------+
| **Default value**  | 5                                  |
+--------------------+------------------------------------+
| **Allowed values** | 0: Disable                         |
+                    +------------------------------------+
|                    | Any number from 1 to 86400         |
+--------------------+------------------------------------+

.. _reference_ossec_analysis_log_level:

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

Configuration
-------------

This block doesn’t appear in the default configuration as default values are loaded instead. The following configuration is an example:

.. code-block:: xml

  <analysis>
    <default_timeframe>80</default_timeframe>
    <stats>
      <percent_diff>75</percent_diff>
    </stats>
    <fts>
      <list_size>300</list_size>
      <min_size_for_str>26</min_size_for_str>
    </fts>
    <geoip_jsonout>0</geoip_jsonout>
    <labels>
      <show_hidden>1</show_hidden>
    </labels>
    <threads>
      <sca>3</sca>
      <hostinfo>1</hostinfo>
      <winevent>7</winevent>
      <rule_matching>0</rule_matching>
    </threads>
    <queue_size>
      <event>200</event>
      <syscheck>10000</syscheck>
      <syscollector>35250</syscollector>
    </queue_size>
    <state_interval>2000</state_interval>
    <log_level>2</log_level>
  </analysis>