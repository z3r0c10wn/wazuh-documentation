.. Copyright (C) 2019 Wazuh, Inc.

.. _reference_ossec_mail:

mail
====

.. topic:: XML section name

	.. code-block:: xml

		<mail>
		</mail>

This section explains how to configure the common options for the email alert sending.

Options
-------

- `strict_checking`_
- `grouping`_
- `full_subject`_
- `geoip`_
- `thread_stack_size`_

strict_checking
^^^^^^^^^^^^^^^

Toggle to enable or disable strict checking. This controls if the end of data message sent to the server is accepted.
If enabled, if the end of data is not accepted by the server an error will be displayed. Otherwise, it will be ignored.

+--------------------+------------------------------------+
| **Default value**  | 1                                  |
+--------------------+------------------------------------+
| **Allowed values** | 0: Disable                         |
+                    +------------------------------------+
|                    | 1: Enable                          |
+--------------------+------------------------------------+

grouping
^^^^^^^^

Toggle to enable or disable grouping of alerts into a single email.

+--------------------+------------------------------------+
| **Default value**  | 1                                  |
+--------------------+------------------------------------+
| **Allowed values** | 0: Disable                         |
+                    +------------------------------------+
|                    | 1: Enable                          |
+--------------------+------------------------------------+

full_subject
^^^^^^^^^^^^

Toggle to enable or disable full subject in alert emails.

+--------------------+------------------------------------+
| **Default value**  | 0                                  |
+--------------------+------------------------------------+
| **Allowed values** | 0: Disable                         |
+                    +------------------------------------+
|                    | 1: Enable                          |
+--------------------+------------------------------------+

geoip
^^^^^

Toggle to enable or disable GeoIP data in alert emails.

+--------------------+------------------------------------+
| **Default value**  | 1                                  |
+--------------------+------------------------------------+
| **Allowed values** | 0: Disable                         |
+                    +------------------------------------+
|                    | 1: Enable                          |
+--------------------+------------------------------------+

thread_stack_size
^^^^^^^^^^^^^^^^^

Defines the stack size for child threads created by the mail process in KiB.

+--------------------+------------------------------------------------------------------------------------------+
| **Default value**  | 8192                                                                                     |
+--------------------+------------------------------------------------------------------------------------------+
| **Allowed values** | Any integer between 2048 and 65536                                                       |
+--------------------+------------------------------------------------------------------------------------------+

Example configuration
---------------------

This block doesn’t appear in the default configuration as default values are loaded instead. The following configuration is an example:

.. code-block:: xml

    <mail>
      <strict_checking>1</strict_checking>
      <grouping>1</grouping>
      <full_subject>0</full_subject>
      <geoip>1</geoip>
      <thread_stack_size>8192<thread_stack_size>
    </mail>
