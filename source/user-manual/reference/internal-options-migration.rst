.. Copyright (C) 2019 Wazuh, Inc.

.. _reference_internal_options_migration:

Internal options migration
==========================

In this section, a table will be shown to ease the migration of the the old :ref:`internal options <reference_internal_options>` to their new equivalences in ``ossec.conf``.

In the following table it's indicated the section and the subsection (it may not have one) where each option belongs and its name in ``ossec.conf``. These three things are related to the option original name in the deprecated ``internal_option`` file.

+-------------------------+----------------+----------------------------+--------------------------------------+
| **Section**             | **Subsection** | **Option**                 | **internal_options**                 |
+-------------------------+----------------+----------------------------+--------------------------------------+
|  <syscheck>             |                |  <sleep>                   |    syscheck.sleep                    |
+-------------------------+----------------+----------------------------+--------------------------------------+
|  <syscheck>             |                |  <sleep_after>             |    syscheck.sleep_after              |
+-------------------------+----------------+----------------------------+--------------------------------------+
|  <syscheck>             |                |  <rt_delay>                |    syscheck.rt_delay                 |
+-------------------------+----------------+----------------------------+--------------------------------------+
|  <syscheck>             |                |  <max_fd_win_rt>           |    syscheck.max_fd_win_rt            |
+-------------------------+----------------+----------------------------+--------------------------------------+
|  <syscheck>             |                |  <max_audit_entries>       |    syscheck.max_audit_entries        |
+-------------------------+----------------+----------------------------+--------------------------------------+
|  <syscheck>             |                |  <default_max_depth>       |    syscheck.default_max_depth        |
+-------------------------+----------------+----------------------------+--------------------------------------+
|  <syscheck>             |                |  <symlink_scan_interval>   |    syscheck.symlink_scan_interval    |
+-------------------------+----------------+----------------------------+--------------------------------------+
|  <syscheck>             |                |  <file_max_size>           |    syscheck.file_max_size            |
+-------------------------+----------------+----------------------------+--------------------------------------+