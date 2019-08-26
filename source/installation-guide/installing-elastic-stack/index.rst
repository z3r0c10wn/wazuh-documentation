.. Copyright (C) 2019 Wazuh, Inc.

.. _installation_elastic:

Installing Elastic Stack
========================

This guide describes the installation of an Elastic Stack server comprised of Filebeat, Elasticsearch, and Kibana. We will illustrate package-based installations of these components.  You can also install them from binary tarballs, however, this is not preferred or supported under Wazuh documentation.

In addition to Elastic Stack components, you will also find the instructions to install and configure the Wazuh app (deployed as a Kibana plugin).

Elastic Stack can be installed either on a single host or be set up on a distributed environment.

- `Single Host Architecture <single-host/index.html>`_

-  `Distributed Environment Architecture <distributed-architecture/index.html>`_



.. toctree::
   :hidden:
   :maxdepth: 2

   single-host/index
   distributed-architecture/index
   protect-installation/index
   elastic_tuning.rst
   automatic_api.rst
   transform_logstash.rst
   distributed-architecture/configure-elasticsearch-cluster.rst
