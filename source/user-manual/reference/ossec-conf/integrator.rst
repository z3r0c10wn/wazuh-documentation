.. Copyright (C) 2019 Wazuh, Inc.

.. _reference_ossec_integrator:

integrator
==========

.. topic:: XML section name

  .. code-block:: xml

    <integrator>
    </integrator>

This configures the common options for the :ref:`integration module <reference_ossec_integration>`.

Options
-------

- `thread_stack_size`_
- `log_level`_

thread_stack_size
^^^^^^^^^^^^^^^^^

Defines the stack size for child threads created by the integrator process in KiB.

+--------------------+------------------------------------------------------------------------------------------+
| **Default value**  | 8192                                                                                     |
+--------------------+------------------------------------------------------------------------------------------+
| **Allowed values** | Any integer between 2048 and 65536                                                       |
+--------------------+------------------------------------------------------------------------------------------+

log_level
---------

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

Example configuration
---------------------

This is an example of configuration of this section with the default values set (it has the same effect as not setting this block):

.. code-block:: xml

  <integrator>
    <log_level>0</log_level>
  </integrator>