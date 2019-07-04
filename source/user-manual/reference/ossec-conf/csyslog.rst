.. Copyright (C) 2019 Wazuh, Inc.

.. _reference_ossec_csyslog:

csyslog
=======

.. topic:: XML section name

	.. code-block:: xml

		<csyslog>
		</csyslog>

This section explains how to configure advanced options for the  :ref:`Syslog output <reference_ossec_syslog_output>` module.

Options
-------

- `thread_stack_size`_

thread_stack_size
^^^^^^^^^^^^^^^^^

Defines the stack size for child threads created by the syslog output process in KiB.

+--------------------+------------------------------------------------------------------------------------------+
| **Default value**  | 8192                                                                                     |
+--------------------+------------------------------------------------------------------------------------------+
| **Allowed values** | Any integer between 2048 and 65536                                                       |
+--------------------+------------------------------------------------------------------------------------------+

Sample configuration
--------------------

This block doesn’t appear in the default configuration as default values are loaded instead. The following configuration is an example:

.. code-block:: xml

    <csylsog>
      <thread_stack_size>8192</thread_stack_size>
    </csyslog>
