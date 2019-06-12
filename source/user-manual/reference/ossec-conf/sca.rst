.. Copyright (C) 2019 Wazuh, Inc.

.. _reference_sec_config_assessment:

sca
===

.. versionadded:: 3.9.0

.. topic:: XML section name

	.. code-block:: xml

		<sca>
		</sca>

Settings to run Security Configuration Assessment scans.

Main options
------------

- `enabled`_
- `skip_nfs`_
- `policies`_

+----------------------+-----------------------------+
| Main options         | Allowed values              |
+======================+=============================+
| `enabled`_           | yes, no                     |
+----------------------+-----------------------------+
| `skip_nfs`_          | yes, no                     |
+----------------------+-----------------------------+
| `policies`_          | N/A                         |
+----------------------+-----------------------------+

Scheduling options
------------------

- `scan_on_start`_
- `interval`_
- `day`_
- `wday`_
- `time`_

+----------------------+-----------------------------+
| Scheduling options   | Allowed values              |
+======================+=============================+
| `scan_on_start`_     | yes, no                     |
+----------------------+-----------------------------+
| `interval`_          | A positive number + suffix  |
+----------------------+-----------------------------+
| `day`_               | A day of the month          |
+----------------------+-----------------------------+
| `wday`_              | A day of the week           |
+----------------------+-----------------------------+
| `time`_              | A time of the day *[hh:mm]* |
+----------------------+-----------------------------+

In the :doc:`SCA documentation<../../capabilities/sec-config-assessment/index>` are shown some cases of using these options.

Other options
-------------

- `request_db_interval`_
- :ref:`commands <sca_commands>`

Main options
------------

- `enabled`_
- `skip_nfs`_
- `policies`_

enabled
^^^^^^^

Enables the module.

+--------------------+-----------------------------+
| **Default value**  | yes                         |
+--------------------+-----------------------------+
| **Allowed values** | yes, no                     |
+--------------------+-----------------------------+

skip_nfs
^^^^^^^^

Enable or disable the scanning of network mounted filesystems (Works on Linux and FreeBSD).
Currently, ``skip_nfs`` will exclude checking files on CIFS or NFS mounts.

+--------------------+---------+
| **Default value**  | yes     |
+--------------------+---------+
| **Allowed values** | yes, no |
+--------------------+---------+

policies
^^^^^^^^

Between ``<policy>`` tags, in this section it can be included policy files to run assessments.

+--------------------+----------------------+
| **Default value**  | n/a                  |
+--------------------+----------------------+
| **Allowed values** | Any YAML policy file |
+--------------------+----------------------+

Attributes

+----------------+---------------------------------------------------------------------------------+
| **enabled**    | Offers the possibility to disable a policy when it has been enabled previously. |
+----------------+---------------------------------------------------------------------------------+

Example

.. code-block:: xml

  <policies>
    <policy>cis_debian_rcl.yml</policy>
    <policy>cis_apache2224_rcl.yml</policy>
    <policy>system_audit_rcl.yml</policy>
  </policies>

  <policies>
    <policy enabled="no">cis_apache2224_rcl.yml</policy>
  </policies>

Scheduling options
------------------

- `scan_on_start`_
- `interval`_
- `day`_
- `wday`_
- `time`_

scan_on_start
^^^^^^^^^^^^^

The SCA module will perform the scan inmediately when started.

+--------------------+---------+
| **Default value**  | yes     |
+--------------------+---------+
| **Allowed values** | yes, no |
+--------------------+---------+

interval
^^^^^^^^

Interval between module executions.

+--------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Default value**  | 12h                                                                                                                                                            |
+--------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Allowed values** | A positive number that should contain a suffix character indicating a time unit, such as, s (seconds), m (minutes), h (hours), d (days), w (weeks), M (months) |
+--------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+

The interval option is conditioned by the following described options ``day``, ``wday`` and ``time``. If none of these options are set, the interval can take any allowed value.

day
^^^

Day of the month to run the scan.

+--------------------+--------------------------+
| **Default value**  | n/a                      |
+--------------------+--------------------------+
| **Allowed values** | Day of the month [1..31] |
+--------------------+--------------------------+

.. note::

	When the ``day`` option is set, the interval value must be a multiple of months. By default, the interval is set to a month.

wday
^^^^

Day of the week to run the scan. This option is **not compatible** with the ``day`` option.

+--------------------+--------------------------+
| **Default value**  | n/a                      |
+--------------------+--------------------------+
| **Allowed values** | Day of the week:         |
|                    |   - sunday/sun           |
|                    |   - monday/mon           |
|                    |   - tuesday/tue          |
|                    |   - wednesday/wed        |
|                    |   - thursday/thu         |
|                    |   - friday/fri           |
|                    |   - saturday/sat         |
+--------------------+--------------------------+

.. note::

	When the ``wday`` option is set, the interval value must be a multiple of weeks. By default, the interval is set to a week.

time
^^^^

Time of the day to run the scan. It has to be represented in the format *hh:mm*.

+--------------------+-----------------------+
| **Default value**  | n/a                   |
+--------------------+-----------------------+
| **Allowed values** | Time of day *[hh:mm]* |
+--------------------+-----------------------+

.. note::

	When only the ``time`` option is set, the interval value must be a multiple of days. By default, the interval is set to a day.

Other options
-------------

request_db_interval
^^^^^^^^^^^^^^^^^^^

Security Configuration Assessment database request interval (minutes). This option sets the maximum waiting time to resend a scan when the database integrity check fails.

+--------------------+--------------------------------------+
| **Default value**  | 5                                    |
+--------------------+--------------------------------------+
| **Allowed values** | Any number between 1 and 60.         |
+--------------------+--------------------------------------+

.. _sca_commands:

Commands subsection
-------------------

remote
^^^^^^

Enable it to accept execute commands from SCA policies pushed from the manager in the shared configuration. Local policies ignore this option.

+--------------------+------------------------------------+
| **Default value**  | 0                                  |
+--------------------+------------------------------------+
| **Allowed values** | 0: Disable                         |
+                    +------------------------------------+
|                    | 1: Enable                          |
+--------------------+------------------------------------+

timeout
^^^^^^^

Default timeout for executed commands during a SCA scan (seconds).

+--------------------+--------------------------------------+
| **Default value**  | 30                                   |
+--------------------+--------------------------------------+
| **Allowed values** | Any number between 1 and 300.        |
+--------------------+--------------------------------------+

Configuration example
---------------------

.. code-block:: xml

      <sca>
        <enabled>yes</enabled>
        <scan_on_start>yes</scan_on_start>
        <time>04:00</time>
        <skip_nfs>yes</skip_nfs>

        <policies>
          <policy>cis_debian_rcl.yml</policy>
          <policy>cis_apache2224_rcl.yml</policy>
          <policy>/var/ossec/etc/shared/test-group/cis_mysql5-6_enterprise_rcl.yml</policy>
        </policies>

        <commands>
          <remote>0</remote>
        </commands>
        <request_db_interval>8</request_db_interval>
      </sca>
