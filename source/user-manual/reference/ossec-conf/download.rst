.. Copyright (C) 2019 Wazuh, Inc.

.. _reference_download:

download
========

.. topic:: XML section name

	.. code-block:: xml

		<download>
		</download>

This section shows how to configure the options for the Wazuh download module.

Options
-------

- `enabled`_

enabled
^^^^^^^

Enables or disables the Wazuh download module.

+--------------------+------------------------------------+
| **Default value**  | 1                                  |
+--------------------+------------------------------------+
| **Allowed values** | 0: Disable                         |
+                    +------------------------------------+
|                    | 1: Enable                          |
+--------------------+------------------------------------+

.. warning::
  If this module is disabled the vulnerability detector CVE's won't be updated.

Example configuration
---------------------

This is an example of configuration of this section with the default values set (it has the same effect as not setting this block):

.. code-block:: xml

  <database>
    <enabled>1</enabled>
  </database>