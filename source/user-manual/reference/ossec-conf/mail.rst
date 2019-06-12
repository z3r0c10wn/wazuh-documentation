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

Example configuration
---------------------

.. code-block:: xml

    <mail>
      <strict_checking>1</strict_checking>
      <grouping>1</grouping>
      <full_subject>0</full_subject>
      <geoip>1</geoip>
    </mail>
