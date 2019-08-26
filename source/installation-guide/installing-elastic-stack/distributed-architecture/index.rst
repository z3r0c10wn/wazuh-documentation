
.. Copyright (C) 2019 Wazuh, Inc.

.. _installation_elastic_distributed_architecture:


Distributed Environment Installation
====================================

Depending on your operating system you can choose to install Elastic Stack from RPM or DEB packages. Consult the table below and choose how to proceed:

+---------------------------------------------------------------------+-----------------------------------------------+
| Type                                                                | Description                                   |
+=====================================================================+===============================================+
| `RPM packages <elastic-server-rpm-distributed-architecture.html>`_  | Install Elastic Stack on CentOS/RHEL/Fedora.  |
+---------------------------------------------------------------------+-----------------------------------------------+
| `DEB packages <elastic-server-deb-distributed-architecture.html>`_  | Install Elastic Stack on Debian/Ubuntu.       |
+---------------------------------------------------------------------+-----------------------------------------------+

After the installation, find below optional steps you may find interesting:

- :ref:`Elasticsearch tuning <elastic_tuning>`
- :ref:`Transform your data with Logstash <transform_logstash>`
- :ref:`Insert a Wazuh API entry automatically <automatic_api>`
- :ref:`Configure a Elasticsearch Cluster <configure_elasticsearch_cluster>`

.. note::

    Currently, the Elastic Stack is only supported on 64-bit operating systems, according to its `Support Matrix <https://www.elastic.co/support/matrix>`_.

.. toctree::
   :hidden:
   :maxdepth: 2

   elastic-server-rpm-distributed-architecture.rst
   elastic-server-deb-distributed-architecture.rst
   
